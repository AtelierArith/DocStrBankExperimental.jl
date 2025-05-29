```
plot_wigner(
    state::QuantumObject{OpType}; 
    library::Union{Val,Symbol}=Val(:Makie), 
    kwargs...
) where {OpType<:Union{Bra,Ket,Operator}
```

Plot the [Wigner quasipropability distribution](https://en.wikipedia.org/wiki/Wigner_quasiprobability_distribution) of `state` using the [`wigner`](@ref) function. 

The `library` keyword argument specifies the plotting library to use, defaulting to [`Makie.jl`](https://github.com/MakieOrg/Makie.jl). 

# Arguments

  * `state::QuantumObject`: The quantum state for which to plot the Wigner distribution.
  * `library::Union{Val,Symbol}`: The plotting library to use. Default is `Val(:Makie)`.
  * `kwargs...`: Additional keyword arguments to pass to the plotting function. See the documentation for the specific plotting library for more information.

!!! note "Import library first"
    The plotting libraries must first be imported before using them with this function.


!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `Val(:Makie)` instead of `:Makie` as the plotting library. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.

