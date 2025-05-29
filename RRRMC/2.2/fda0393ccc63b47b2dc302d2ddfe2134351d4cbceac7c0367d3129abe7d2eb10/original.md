```
wtmMC(X::AbstractGraph, β::Real, samples::Integer; keywords...)
```

Same as [`standardMC`](@ref), but uses the rejection-free waiting-time method by Dall and Sibani. It is similar to [`bklMC`](@ref).

The return values and the keyword arguments are *almost* the same as [`standardMC`](@ref), see the usage examples for that function. However, the waiting time method uses an internal "global time" variable, which takes the place of the "iterations" counter of [`standardMC`](@ref) and of [`bklMC`](@ref). Thus, this function has two differences with respect to the other samplers in the module:

  * the function takes a `samples` integer argument, with the maximum number of samples which will be collected.
  * the `step` keyword argument is of type `Float64` instead of integer (default value = `1.0`; you'll probably want to change this). The `step` is measured in terms of the global time variable and is scaled with the size of the problem `N`.

The total number of samples actually collected can still be less than `samples` if the `hook` function from the keyword arguments returns `false` earlier.
