```
DimIndices <: AbstractArray

DimIndices(x)
DimIndices(dims::Tuple)
DimIndices(dims::Dimension)
```

Like `CartesianIndices`, but for `Dimension`s. Behaves as an `Array` of `Tuple` of `Dimension(i)` for all combinations of the axis indices of `dims`.

This can be used to view/index into arbitrary dimensions over an array, and is especially useful when combined with `otherdims`, to iterate over the indices of unknown dimension.

`DimIndices` can be used directly in `getindex` like `CartesianIndices`, and freely mixed with individual `Dimension`s or tuples of `Dimension`.

## Example

Index a `DimArray` with `DimIndices`.

Notice that unlike CartesianIndices, it doesn't matter if the dimensions are not in the same order. Or even if they are not all contained in each.

```jldoctest; setup = :(using DimensionalData, Random; Random.seed!(123))
julia> A = rand(Y(0.0:0.3:1.0), X('a':'f'))
┌ 4×6 DimArray{Float64, 2} ┐
├──────────────────────────┴──────────────────────────────── dims ┐
  ↓ Y Sampled{Float64} 0.0:0.3:0.9 ForwardOrdered Regular Points,
  → X Categorical{Char} 'a':1:'f' ForwardOrdered
└─────────────────────────────────────────────────────────────────┘
 ↓ →   'a'       'b'       'c'        'd'        'e'       'f'
 0.0  0.9063    0.253849  0.0991336  0.0320967  0.774092  0.893537
 0.3  0.443494  0.334152  0.125287   0.350546   0.183555  0.354868
 0.6  0.745673  0.427328  0.692209   0.930332   0.297023  0.131798
 0.9  0.512083  0.867547  0.136551   0.959434   0.150155  0.941133

julia> di = DimIndices((X(1:2:4), Y(1:2:4)))
┌ 2×2 DimIndices{Tuple{X{Int64}, Y{Int64}}, 2} ┐
├──────────────────────────────────────── dims ┤
  ↓ X 1:2:3,
  → Y 1:2:3
└──────────────────────────────────────────────┘
 ↓ →  1                3
 1     (↓ X 1, → Y 1)   (↓ X 1, → Y 3)
 3     (↓ X 3, → Y 1)   (↓ X 3, → Y 3)

julia> A[di] # Index A with these indices
┌ 2×2 DimArray{Float64, 2} ┐
├──────────────────────────┴──────────────────────────────── dims ┐
  ↓ Y Sampled{Float64} 0.0:0.6:0.6 ForwardOrdered Regular Points,
  → X Categorical{Char} 'a':2:'c' ForwardOrdered
└─────────────────────────────────────────────────────────────────┘
 ↓ →   'a'       'c'
 0.0  0.9063    0.0991336
 0.6  0.745673  0.692209
```
