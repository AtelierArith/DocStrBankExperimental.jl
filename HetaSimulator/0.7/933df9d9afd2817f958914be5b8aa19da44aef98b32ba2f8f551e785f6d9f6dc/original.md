```
DataFrame(s::Simulation; 
  vars=observables(s), parameters_output::Vector{Symbol}=Symbol[], iter::Union{Int,Nothing}=nothing)
```

Converts simulation results of type `SimResult`, `MCResult`, etc  to `DataFrame`.

Example: `DataFrame(s)`

Arguments:

  * `s` : simulation results of type [`SimResult`](@ref), [`MCResult`](@ref) or `Vector` containing them
  * `parameters_output` : parameters provided as kwarg `parameters` to `sim` or `mc` functions, which should be included in `DataFrame`. Default is `empty`
  * `iter` : `Int` iteration id, which should be included in `DataFrame`. Default is `nothing`
