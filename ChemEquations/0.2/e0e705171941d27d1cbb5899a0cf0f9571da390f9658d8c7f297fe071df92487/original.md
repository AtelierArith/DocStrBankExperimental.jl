```julia
balancematrix(
    equation::ChemEquations.ChemEquation{T<:(Union{Complex{S}, S} where S<:Integer)};
    fractions
) -> Any

```

Same as [`balancematrix(::ChemEquation)`](@ref), but for a chemical equation with integer coefficients.

By default, the solutions of integer matrices are displayed as integers. If `fractions` is true, they will be displayed as rational fractions instead.
