```
transform_linear_forward(model::AbstractImageModel, x::AbstractArray)
```

Convert the input array of the image model parameters into the corresponding array of the linear-scale intensity map. This is supposed to be the inverse funciton of $transform_linear_inverse$.

# Arguments

  * `model::AbstractImageModel`: the image model
  * `x::AbstractArray`: the array of the image model parameters
