```
model_infill(search_range::Vector{Tuple{Float64,Float64}},plan::AbstractArray{T,2},
samples::AbstractArray{T,2},sm_interpolant; options::Options=Options()) where T
```

Infill function that calculates the location of new samples based on the supplied options. The returned options are updated to facilitate cycling through the infill objective functions.

...

# Arguments

  * `search_range::Vector{Tuple{Float64,Float64}`:   a vector of tuples containing the lower and upper limits   for each dimension. `length(search_range)` is equal to number   of dimensions.
  * `plan::AbstractArray{T,2}`:    sample locations where each column corresponds to the location of one point.   `size(plan) = (num_dimensions,num_samples)`.
  * `samples::AbstractArray{T,2}`:   function value at each sample location. each column contains one value from   the corresponding plan location. `size(samples) = (1,num_samples)`.
  * `options=Options()`:    all options available to customize the surrogate infill.

...
