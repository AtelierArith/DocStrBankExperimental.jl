```
surrogate_model(plan::AbstractArray{T,2}, samples::AbstractArray{T,2}; options=Options()) where T
```

Returns a surrogate model function based on an optimized Radial Basis Function interpolant. Depending on the supplied options; the kernel, kernel width and scaling of  input data is optimized.

...

# Arguments

  * `plan::AbstractArray{T,2}`:    sample locations where each column corresponds to the location of one point.   `size(plan) = (num_dimensions,num_samples)`.
  * `samples::AbstractArray{T,2}`:   function value at each sample location. each column contains one value from   the corresponding plan location. `size(samples) = (1,num_samples)`.
  * `options=Options()`:    all options available to customize the surrogate optimization.

...
