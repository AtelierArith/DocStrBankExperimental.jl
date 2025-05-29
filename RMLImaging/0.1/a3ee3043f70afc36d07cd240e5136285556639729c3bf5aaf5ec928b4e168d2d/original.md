```
transform_linear_forward(model::AbstractImageModel, x::AbstractArray)
```

Convert the input array of the linear-scale intensity map into the array of the  corresponding model parameters. This is supposed to be the inverse funciton of $transform_linear_forward$.

# Arguments

  * `model::AbstractImageModel`: the image model
  * `x::AbstractArray`: the array of the linear-scale intensity map
