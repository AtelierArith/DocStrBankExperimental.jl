```
charts, admap, act_to_global = assemblydata(basis; onlyactives=true)
```

Given a `basis` this function returns a data structure containing the information required for matrix assemble, that is, the vector `charts` containing `Simplex` elements, a variable `admap` of type `AssemblyData`, and a mapping from indices of actively used simplices to global simplices.

When `onlyactives` is `true`, another layer of indices is introduced to filter out all cells of the mesh that are not in the union of the support of the basis functions (i.e., when the basis functions are defined only on a part of the mesh).

`admap` is, in essence, a three-dimensional array of named tuples, which, by wrapping it in the struct `AssemblyData`, allows the definition of iterators. The tuple consists of the two entries

```
admap[i,r,c].globalindex
admap[i,r,c].coefficient
```

Here, `c` and `r` are indices in the iterable set of (active) simplices and the set of shape functions on each cell/simplex: `r` ranges from 1 to the number of shape functions on a cell/simplex, `c` ranges from 1 to the number of active simplices, and `i` ranges from 1 to the number of maximal number of basis functions, where any of the shape functions contributes to. 

For example, for continuous piecewise linear lagrange functions (c0d1), each of the three shape functions on a triangle are associated with exactly one Lagrange function, and therefore `i` is limited to 1.

*Note*: When `onlyactives=false`, the indices `c` correspond to the position of the corresponding cell/simplex whilst iterating over `geometry(basis)`. When `onlyactives=true`, then `act_to_global(c)` correspond to the position of the corresponding cell/simplex whilst iterating over `geometry(basis)`.

For a triplet `(i,r,c)`, `globalindex` is the index in the `basis` of the `i`th basis function that has a contribution from shape function `r` on (active) cell/simplex `c`. `coefficient` is the coefficient of that contribution in the linear combination defining that basis function in terms of shape function.
