```
DimStack <: AbstractDimStack

DimStack(data::AbstractDimArray...)
DimStack(data::Tuple{Vararg{AbstractDimArray}})
DimStack(data::NamedTuple{Keys,Vararg{AbstractDimArray}})
DimStack(data::NamedTuple, dims::DimTuple; metadata=NoMetadata())
```

DimStack holds multiple objects sharing some dimensions, in a `NamedTuple`.

Notably, their behaviour lies somewhere between a `DimArray` and a `NamedTuple`:

  * indexing with a `Symbol` as in `dimstack[:symbol]` returns a `DimArray` layer.
  * iteration amd `map` are apply over array layers, as indexed with a `Symbol`.
  * `getindex` or `view` with `Int`, `Dimension`s or `Selector`s that resolve to `Int` will   return a `NamedTuple` of values from each layer in the stack.   This has very good performace, and avoids the need to always use `map`.
  * `getindex` or `view` with a `Vector` or `Colon` will return another `DimStack` where   all data layers have been sliced.
  * `setindex!` must pass a `Tuple` or `NamedTuple` maching the layers.
  * many base and `Statistics` methods (`sum`, `mean` etc) will work as for a `DimArray`   again removing the need to use `map`.

For example, here we take the mean over the time dimension for all layers :

```julia
mean(mydimstack; dims=Ti)
```

And this equivalent to:

```julia
map(A -> mean(A; dims=Ti), mydimstack)
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
X Symbol[:a, :b],
Y 10.0:10.0:30.0

julia> da1 = DimArray(1A, dimz; name=:one);

julia> da2 = DimArray(2A, dimz; name=:two);

julia> da3 = DimArray(3A, dimz; name=:three);

julia> s = DimStack(da1, da2, da3);

julia> s[At(:b), At(10.0)]
(one = 4.0, two = 8.0, three = 12.0)

julia> s[X(At(:a))] isa DimStack
true
```
