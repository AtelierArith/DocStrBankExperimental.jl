```julia
find_representation(
    symeigs::AbstractVector{<:AbstractVector{<:Number}},
    irs::AbstractVector{<:Crystalline.AbstractIrrep};
    ...
) -> Any
find_representation(
    symeigs::AbstractVector{<:AbstractVector{<:Number}},
    irs::AbstractVector{<:Crystalline.AbstractIrrep},
    bands::AbstractVector{Int64};
    ...
) -> Any
find_representation(
    symeigs::AbstractVector{<:AbstractVector{<:Number}},
    irs::AbstractVector{<:Crystalline.AbstractIrrep},
    bands::AbstractVector{Int64},
    assert_return_T::Type{<:Union{AbstractFloat, Integer}};
    kws...
) -> Any

```

Given a set of *band*-resolved symmetry eigenvalues `symeigs`, a set of irreps `irs`, and a selection of band indices `bands` into `symeigs`, return the associated multiplicities of corresponding to `irs`.

The `symeigs` argument is a vector of symmetry eigenvalues, or symmetry characters, for individual bands. The `symeigs[n][i]`th entry gives the symmetry eigenvalue $x_n(g_i)$ of the `n`th band and the $g_i =$ `group(irs)[i]` symmetry operation, with:

````
```math
x_n(g_i) = \langle \psi_n | g_i | \psi_n \rangle
```
````

If unset, `bands` contains all bands in `symeigs`, i.e., is equal to `eachindex(symeigs)`.

## Keyword arguments

  * `kws`: Additional keyword arguments passed to [`find_representation(::AbstractVector{<:Number})`](@ref) (e.g., `αβγ`, `atol`, `maxresnorm`).
