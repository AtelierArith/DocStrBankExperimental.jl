```
modify(f, A::AbstractDimArray) => AbstractDimArray
modify(f, s::AbstractDimStack) => AbstractDimStack
modify(f, dim::Dimension) => Dimension
modify(f, x, lookupdim::Dimension) => typeof(x)
```

Modify the parent data, rebuilding the object wrapper without change. `f` must return a `AbstractArray` of the same size as the original.

This method is mostly useful as a way of swapping the parent array type of an object.

## Example

If we have a previously-defined `DimArray`, we can copy it to an Nvidia GPU with:

```julia
A = DimArray(rand(100, 100), (X, Y))
modify(CuArray, A)
```

This also works for all the data layers in a `DimStack`.
