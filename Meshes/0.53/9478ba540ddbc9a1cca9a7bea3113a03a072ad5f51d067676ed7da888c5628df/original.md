```
connect(indices, [PL])
```

Connect a list of `indices` from a global vector of [`Point`](@ref) into a [`Polytope`](@ref) of type `PL`.

The type `PL` can be a [`Ngon`](@ref) in which case the length of the indices is used to identify the actual polytope type.

Finally, the type `PL` can be ommitted. In this case, the indices are assumed to be connected as a [`Ngon`](@ref) or as a [`Segment`](@ref).

## Examples

Connect indices into a Triangle:

```julia
connect((1,2,3), Triangle)
```

Connect indices into N-gons, a `Triangle` and a `Quadrangle`:

```julia
connect.([(1,2,3), (2,3,4,5)], Ngon)
```

Connect indices into N-gon or segment:

```julia
connect((1,2)) # Segment
connect((1,2,3)) # Triangle
connect((1,2,3,4)) # Quadrangle
```
