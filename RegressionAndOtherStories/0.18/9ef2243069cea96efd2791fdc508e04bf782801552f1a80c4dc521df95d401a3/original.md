ros_data()

Base part of the path to datafiles in the R package ROS-Examples. Return "" if `env_var` is not present in ENV.

## Positional argument

```julia
* `dataset::Union{AbstractString, Missing}` # Path to data in ROS-Examples
```

### Keyword arguments

```julia
* `env_var = "JULIA_ROS_HOME"` # Environment variable name
```

### Returns

```julia
* `path::AbstractString` # Path or "".
```

# Extended help

Examples:

```julia
ros_path()
ros_path("HDI")
```
