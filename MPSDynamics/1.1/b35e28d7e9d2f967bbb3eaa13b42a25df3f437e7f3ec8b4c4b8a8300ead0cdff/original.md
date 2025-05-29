```
randmps(tree::Tree, physdims, Dmax::Int, T::Type{<:Number} = Float64)
```

Construct a random, right-normalised, tree-MPS, with structure given by tree and max bond-dimension given by `Dmax`.

The local Hilbert space dimensions are specified by physdims which can either be of type `Dims{length(tree)}`, specifying the dimension of each site, or of type `Int`, in which case the same local dimension is used for every site.
