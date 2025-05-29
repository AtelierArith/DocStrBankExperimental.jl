```
DimSelectors <: AbstractArray

DimSelectors(x; selectors, atol...)
DimSelectors(dims::Tuple; selectors, atol...)
DimSelectors(dims::Dimension; selectors, atol...)
```

Like [`DimIndices`](@ref), but returns `Dimensions` holding the chosen [`Selector`](@ref)s.

Indexing into another `AbstractDimArray` with `DimSelectors` is similar to doing an interpolation.

## Keywords

  * `selectors`: `Near`, `At` or `Contains`, or a mixed tuple of these. `At` is the default, meaning only exact or within `atol` values are used.
  * `atol`: used for `At` selectors only, as the `atol` value. Ignored where    `atol` is set inside individual `At` selectors.

## Example

Here we can interpolate a `DimArray` to the lookups of another `DimArray` using `DimSelectors` with `Near`. This is essentially equivalent to nearest neighbour interpolation.

```jldoctest; setup = :(using DimensionalData, Random; Random.seed!(123))
julia> A = rand(X(1.0:3.0:30.0), Y(1.0:5.0:30.0), Ti(1:2));

julia> target = rand(X(1.0:10.0:30.0), Y(1.0:10.0:30.0));

julia> A[DimSelectors(target; selectors=Near), Ti=2]
┌ 3×3 DimArray{Float64, 2} ┐
├──────────────────────────┴──────────────────────────────────────── dims ┐
  ↓ X Sampled{Float64} [1.0, 10.0, 22.0] ForwardOrdered Irregular Points,
  → Y Sampled{Float64} [1.0, 11.0, 21.0] ForwardOrdered Irregular Points
└─────────────────────────────────────────────────────────────────────────┘
  ↓ →  1.0        11.0       21.0
  1.0  0.691162    0.218579   0.539076
 10.0  0.0303789   0.420756   0.485687
 22.0  0.0967863   0.864856   0.870485
```

Using `At` would make sure we only use exact interpolation, while `Contains` with sampling of `Intervals` would make sure that each values is taken only from an Interval that is present in the lookups.
