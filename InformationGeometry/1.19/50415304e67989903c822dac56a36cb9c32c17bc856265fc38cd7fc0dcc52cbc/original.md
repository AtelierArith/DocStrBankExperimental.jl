The `HyperCube` type is used to specify a cuboid region in the form of a cartesian product of $N$ real intervals, thereby offering a convenient way of passing domains for integration or plotting between functions. A `HyperCube` object `cube` type has two fields: `cube.L` and `cube.U` which are two vectors which respectively store the lower and upper boundaries of the real intervals in order. Examples for constructing `HyperCube`s:

```julia
HyperCube([[1,3],[π,2π],[-500,100]])
HyperCube([1,π,-500],[3,2π,100])
HyperCube([[-1,1]])
HyperCube([-1,1])
HyperCube(collect([-7,7.] for i in 1:3))
```

Examples of quantities that can be computed from and operations involving a `HyperCube` object `X`:

```julia
CubeVol(X)
TranslateCube(X,v::AbstractVector)
CubeWidths(X)
```
