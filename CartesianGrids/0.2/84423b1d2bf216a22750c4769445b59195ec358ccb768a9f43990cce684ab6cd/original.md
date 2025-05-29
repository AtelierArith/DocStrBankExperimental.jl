```
coordinates(w::GridData;[dx=1.0],[I0=(1,1)])
```

Return a tuple of the ranges of the physical coordinates in each direction for grid data `w`. If `w` is of `Nodes` type, then it returns a tuple of the form `xg,yg`. If `w` is of `Edges` or `NodePair` type, then it returns a tuple of the form `xgu,ygu,xgv,ygv`.

The optional keyword argument `dx` sets the grid spacing; its default is `1.0`. The optional keyword `I0` accepts a tuple of integers to set the index pair of the primal nodes that coincide with the origin. The default is `(1,1)`.

# Example

```jldoctest
julia> w = Nodes(Dual,(12,22));

julia> xg, yg = coordinates(w,dx=0.1)
(-0.05:0.1:1.05, -0.05:0.1:2.0500000000000003)
```
