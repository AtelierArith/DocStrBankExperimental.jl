```
DimStack <: AbstractDimStack

DimStack(data::AbstractDimArray...; kw...)
DimStack(data::Union{AbstractArray,Tuple,NamedTuple}, [dims::DimTuple]; kw...)
DimStack(data::AbstractDimArray; layersfrom, kw...)
```

DimStack holds multiple objects sharing some dimensions, in a `NamedTuple`.

## Arguments

  * `data`: `AbstractDimArray` or an `AbstractArray`, `Tuple` or `NamedTuple` of `AbstractDimArray`s or `AbstractArray`s.
  * `dims`: `DimTuple` of `Dimension`s. Required when `data` is not `AbstractDimArray`s.

## Keywords

  * `name`: `Array` or `Tuple` of `Symbol` names for each layer. By default   the names of `DimArrays` are or keys of a `NamedTuple` are used,    or `:layer1`, `:layer2`, etc.
  * `metadata`: `AbstractDict` or `NamedTuple` metadata for the stack.
  * `layersfrom`: A dimension to slice layers from if data is a single   `DimArray`. Defaults to `nothing`.

(These are for advanced uses)

  * `layerdims`: `Array`, `Tuple` or `NamedTuple` of dimension tuples to match the   dimensions of each layer. Dimensions in `layerdims` must also be in `dims`.
  * `layermetadata`: `Array`, `Tuple` or `NamedTuple` of metadata for each layer.
  * `refdims`: `NamedTuple` of `Dimension`s for each layer, `()` by default.

## Details

`DimStack` behaviour lies somewhere between a `DimArray` and a `NamedTuple`:

  * indexing with a `Symbol` as in `dimstack[:layername]` or using `getproperty`    `dimstack.layername` returns a `DimArray` layer.
  * A `DimStack` iterates `NamedTuple`s corresponding to the value of each layer. This means functions like `map`, `broadcast`, and `collect` behave as if the `DimStack` were a `DimArray{<:NamedTuple}`
  * `getindex` or `view` with a `Vector` or `Colon` will return another `DimStack` where   all data layers have been sliced, unless this resolves to a single element, in which case    `getindex` returns a `NamedTuple`
  * `setindex!` must pass a `Tuple` or `NamedTuple` matching the layers.
  * many base and `Statistics` methods (`sum`, `mean` etc) will work as for a `DimArray`,   applied to all layers separately.
  * to apply a function to each layer of a `DimStack`, use [`maplayers`](@ref).

```julia
function DimStack(A::AbstractDimArray;
    layersfrom=nothing, name=nothing, metadata=metadata(A), refdims=refdims(A), kw...
)
```

For example, here we take the mean over the time dimension for all layers:

```julia
mean(mydimstack; dims=Ti)
```

And this equivalent to:

```julia
maplayers(A -> mean(A; dims=Ti), mydimstack)
```

This design gives succinct code when working with many-layered, mixed-dimension objects.

But it may be jarring initially - the most surprising outcome is that `dimstack[1]` will return a `NamedTuple` of values for the first index in all layers, while `first(dimstack)` will return the first value of the iterator - the `DimArray` for the first layer.

`DimStack` can be constructed from multiple `AbstractDimArray` or a `NamedTuple` of `AbstractArray` and a matching `dims` tuple.

Most `Base` and `Statistics` methods that apply to `AbstractArray` can be used on all layers of the stack simulataneously. The result is a `DimStack`, or a `NamedTuple` if methods like `mean` are used without `dims` arguments, and return a single non-array value.

## Example

```jldoctest
julia> using DimensionalData

julia> A = [1.0 2.0 3.0; 4.0 5.0 6.0];

julia> dimz = (X([:a, :b]), Y(10.0:10.0:30.0))
(↓ X [:a, :b],
→ Y 10.0:10.0:30.0)

julia> da1 = DimArray(1A, dimz; name=:one);

julia> da2 = DimArray(2A, dimz; name=:two);

julia> da3 = DimArray(3A, dimz; name=:three);

julia> s = DimStack(da1, da2, da3);

julia> s[At(:b), At(10.0)]
(one = 4.0, two = 8.0, three = 12.0)

julia> s[X(At(:a))] isa DimStack
true
```
