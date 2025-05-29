```
plot_fock_distribution(
    ρ::QuantumObject{SType};
    library::Union{Val, Symbol} = Val(:Makie),
    kwargs...
) where {SType<:Union{Ket,Operator}}
```

Plot the [Fock state](https://en.wikipedia.org/wiki/Fock_state) distribution of `ρ`. 

The `library` keyword argument specifies the plotting library to use, defaulting to [`Makie`](https://github.com/MakieOrg/Makie.jl). 

# Arguments

  * `ρ::QuantumObject`: The quantum state for which to plot the Fock state distribution.
  * `library::Union{Val,Symbol}`: The plotting library to use. Default is `Val(:Makie)`.
  * `kwargs...`: Additional keyword arguments to pass to the plotting function. See the documentation for the specific plotting library for more information.

!!! note "Import library first"
    The plotting libraries must first be imported before using them with this function.


!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `Val(:Makie)` instead of `:Makie` as the plotting library. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.

