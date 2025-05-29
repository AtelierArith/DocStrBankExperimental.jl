```julia
smolyak_basis(
    univariate_family,
    grid_kind,
    smolyak_parameters,
    _
)

```

Create a sparse Smolyak basis.

# Arguments

  * `univariate_family`: should be a callable that takes a `grid_kind` and a `dimension` parameter, eg `Chebyshev`.
  * `grid_kind`: the grid kind, eg `InteriorGrid()` etc.
  * `smolyak_parameters`: the Smolyak grid specification parameters, see [`SmolyakParameters`](@ref).
  * `N`: the dimension. wrapped in a `Val` for type stability, a convenience constructor also takes integers.

## Example

```jldoctest
julia> basis = smolyak_basis(Chebyshev, InteriorGrid(), SmolyakParameters(3), 2)
Sparse multivariate basis on ℝ²
  Smolyak indexing, ∑bᵢ ≤ 3, all bᵢ ≤ 3, dimension 81
  using Chebyshev polynomials (1st kind), InteriorGrid(), dimension: 27

julia> dimension(basis)
81

julia> domain(basis)
[-1,1]²
```

## Properties

*Grids nest*: increasing arguments of `SmolyakParameters` result in a refined grid that contains points of the cruder grid.
