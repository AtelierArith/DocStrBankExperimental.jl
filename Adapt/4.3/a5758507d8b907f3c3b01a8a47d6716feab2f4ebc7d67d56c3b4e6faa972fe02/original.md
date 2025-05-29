```
WrappedArray{T,N,Src,Dst}
```

Union-type that encodes all array wrappers known by Adapt.jl. Typevars `T` and `N` encode the type and dimensionality of the resulting container.

Two additional typevars are used to encode the parent array type: `Src` when the wrapper uses the parent array as a source, but changes its properties (e.g. `SubArray{T,1,Array{T,2}` changes `N`), and `Dst` when those properties are copied and thus are identical to the destination wrapper's properties (e.g. `Transpose{T,Array{T,N}}` has the same dimensionality as the inner array). When creating an alias for this type, e.g. `WrappedSomeArray{T,N} = WrappedArray{T,N,...}` the `Dst` typevar should typically be set to `SomeArray{T,N}` while `Src` should be more lenient, e.g., `SomeArray`.

Only use this type for dispatch purposes. To convert instances of an array wrapper, use [`adapt`](@ref).
