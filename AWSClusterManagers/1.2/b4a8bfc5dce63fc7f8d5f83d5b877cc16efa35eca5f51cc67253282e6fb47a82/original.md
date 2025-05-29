```
DockerManager(num_workers; kwargs...)
```

A cluster manager which spawns workers via a locally running [Docker](https://docs.docker.com/) daemon service. Typically used on a single machine to debug multi-machine Julia code.

In order to make a local Docker cluster you'll need to have an available Docker image that has Julia, a version of AWSClusterManagers which includes DockerManager, and the docker cli all baked into the image.

You can then create a Docker container which is capable of spawning additional Docker containers via:

docker run –network=host -v /var/run/docker.sock:/var/run/docker.sock –rm -it <image> julia

**Note**: The host networking is required for the containers to be able to intercommunicate. The Docker host's UNIX socket needs to be forwarded so we can allow the container to communicate with host Docker process.

## Arguments

  * `num_workers::Int`: The number of workers to spawn

## Keywords

  * `image::AbstractString`: The docker image to run.
  * `timeout::Second`: The maximum number of seconds to wait for workers to become available before aborting.

## Examples

```julia
julia> addprocs(DockerManager(4, "myproject:latest"))
```
