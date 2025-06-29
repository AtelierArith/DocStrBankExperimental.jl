```
set(x, val)
set(x, args::Pairs...) => x with updated field/s
set(x, args...; kw...) => x with updated field/s
set(x, args::Tuple{Vararg{Dimension}}; kw...) => x with updated field/s

set(dim::Dimension, index::AbstractArray) => Dimension
set(dim::Dimension, lookup::Lookup) => Dimension
set(dim::Dimension, lookupcomponent::LookupTrait) => Dimension
set(dim::Dimension, metadata::AbstractMetadata) => Dimension
```

Set the properties of an object, its internal data or the traits of its dimensions and lookup index.

As DimensionalData is so strongly typed you do not need to specify what field of a [`Lookup`](@ref) to `set` - there is no ambiguity.

To set fields of a `Lookup` you need to specify the dimension. This can be done using `X => val` pairs, `X = val` keyword arguments, or `X(val)` wrapped arguments.

You can also set the fields of all dimensions by simply passing a single [`Lookup`](@ref) or lookup trait - it will be set for all dimensions.

When a `Dimension` or `Lookup` is passed to `set` to replace the existing ones, fields that are not set will keep their original values.

## Notes:

Changing a lookup index range/vector will also update the step size and order where applicable.

Setting the [`Order`](@ref) like `ForwardOrdered` will *not* reverse the array or dimension to match. Use `reverse` and [`reorder`](@ref) to do this.

## Examples

```jldoctest set
julia> using DimensionalData; const DD = DimensionalData;

julia> da = DimArray(zeros(3, 4), (custom=10.0:010.0:30.0, Z=-20:010.0:10.0));

julia> set(da, ones(3, 4))
┌ 3×4 DimArray{Float64, 2} ┐
├──────────────────────────┴──────────────────────────────────────── dims ┐
  ↓ custom Sampled{Float64} 10.0:10.0:30.0 ForwardOrdered Regular Points,
  → Z      Sampled{Float64} -20.0:10.0:10.0 ForwardOrdered Regular Points
└─────────────────────────────────────────────────────────────────────────┘
  ↓ →  -20.0  -10.0  0.0  10.0
 10.0    1.0    1.0  1.0   1.0
 20.0    1.0    1.0  1.0   1.0
 30.0    1.0    1.0  1.0   1.0
```

Change the `Dimension` wrapper type:

```jldoctest set
julia> set(da, :Z => Ti, :custom => Z)
┌ 3×4 DimArray{Float64, 2} ┐
├──────────────────────────┴──────────────────────────────────── dims ┐
  ↓ Z  Sampled{Float64} 10.0:10.0:30.0 ForwardOrdered Regular Points,
  → Ti Sampled{Float64} -20.0:10.0:10.0 ForwardOrdered Regular Points
└─────────────────────────────────────────────────────────────────────┘
  ↓ →  -20.0  -10.0  0.0  10.0
 10.0    0.0    0.0  0.0   0.0
 20.0    0.0    0.0  0.0   0.0
 30.0    0.0    0.0  0.0   0.0
```

Change the lookup `Vector`:

```jldoctest set
julia> set(da, Z => [:a, :b, :c, :d], :custom => [4, 5, 6])
┌ 3×4 DimArray{Float64, 2} ┐
├──────────────────────────┴──────────────────────────────────────── dims ┐
  ↓ custom Sampled{Int64} [4, 5, 6] ForwardOrdered Regular Points,
  → Z      Sampled{Symbol} [:a, :b, :c, :d] ForwardOrdered Regular Points
└─────────────────────────────────────────────────────────────────────────┘
 ↓ →   :a   :b   :c   :d
 4    0.0  0.0  0.0  0.0
 5    0.0  0.0  0.0  0.0
 6    0.0  0.0  0.0  0.0
```

Change the `Lookup` type:

```jldoctest set
julia> set(da, Z=DD.NoLookup(), custom=DD.Sampled())
┌ 3×4 DimArray{Float64, 2} ┐
├──────────────────────────┴──────────────────────────────────────── dims ┐
  ↓ custom Sampled{Float64} 10.0:10.0:30.0 ForwardOrdered Regular Points,
  → Z
└─────────────────────────────────────────────────────────────────────────┘
 10.0  0.0  0.0  0.0  0.0
 20.0  0.0  0.0  0.0  0.0
 30.0  0.0  0.0  0.0  0.0
```

Change the `Sampling` trait:

```jldoctest set
julia> set(da, :custom => DD.Irregular(10, 12), Z => DD.Regular(9.9))
┌ 3×4 DimArray{Float64, 2} ┐
├──────────────────────────┴────────────────────────────────────────── dims ┐
  ↓ custom Sampled{Float64} 10.0:10.0:30.0 ForwardOrdered Irregular Points,
  → Z      Sampled{Float64} -20.0:10.0:10.0 ForwardOrdered Regular Points
└───────────────────────────────────────────────────────────────────────────┘
  ↓ →  -20.0  -10.0  0.0  10.0
 10.0    0.0    0.0  0.0   0.0
 20.0    0.0    0.0  0.0   0.0
 30.0    0.0    0.0  0.0   0.0
```
