# PyRoboSim Rigel example

This repository contains an example of how to use Rigel with a more complex ROS application.

The [original project](https://github.com/sea-bass/pyrobosim) is maintained by [Sebastian Castro](https://github.com/sea-bass/). A copy of the original license can be found [here](./LICENSE-original.md). Refer to the [full documentation](https://pyrobosim.readthedocs.io/) of PyRoboSim for setup, usage, and other concepts.

## Usage

To get started, first you need to modify the `Rigelfile` with your remote registry. Modify the `image` and `image_name` variables to match your desired destination. You need to export a few environment variables or set them as CI secrets:
 
- `COSIGN_PASSWORD` to use a password for signing your containers
- `REGISTRY_USERNAME` and `REGISTRY_PASSWORD` to match your registry login credentials:
    - Use your DockerHub password or a personal access token for accessing the `docker.io` registry 
    - Use a Github personal access token when accessing the `ghcr.io` registry

To generate the Dockerfile for this project

```bash
rigel run job dockerfile
```

To build the project and push to the remote registry 

```bash
rigel run job build
```

To run unit tests inside the project 

```bash
rigel run job build
```

To run some demo nodes from `pyrobosim_ros`, modify the `DISPLAY` variable to your system's, and use the `run-demo` and `run-demo-multirobot` jobs

```bash
xhost +local:docker # Ensure docker can access the DISPLAY
rigel run job run-demo
```

To sign your remote image

```bash
rigel run sequence sign-and-verify
```
