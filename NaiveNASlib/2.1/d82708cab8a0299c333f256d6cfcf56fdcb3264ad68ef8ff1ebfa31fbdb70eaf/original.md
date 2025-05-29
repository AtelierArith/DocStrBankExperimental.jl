```
nout(v)
```

Return the number of output neurons of vertex `v`. 

This is typically the number of rows/columns of a parameter `Matrix` for fully connected layers or the number of output channels in a convolutional layer. 

Note that NaiveNASlib does not have the capability to figure this out by itself so this must be provided by the function wrapped in the vertex. For [`SizeTransparent`](@ref) vertices, NaiveNASlib will default to computing `nout(v)` from the sizes of the inputs.

There are three ways to implement `nin` for a function/callable `f` of type `F`:

```
1. nout(f::F)
2. nout(st::ST, f) and st = shapetrait(f)
3. nout(f::F, t::MutationTrait, v::AbstractVertex)
```

While `1` is the most straight forward, `2` can be useful of there are many different `f`s which happen to share a common method for determining the size. Option `3` is when the implementation might want to use other information from `v` or `t` and is left as an escape hatch.
