ros_data()

Construct the path to a datafile in the R package ROS-Examples. Return "" if `env_var` is not present in ENV.

## Positional argument

```julia
* `dataset::AbstractString`
* `parts::Vector{AbstractString}` # Path to data file in 
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
ros_data()
ros_data("HDI", "hdi.dat")
```
