```
overapproximate(cap::Intersection{N,
                                  <:CartesianProductArray,
                                  <:AbstractPolyhedron},
                ::Type{<:CartesianProductArray}, oa) where {N}
```

Overapproximate the intersection of a Cartesian product of a finite number of sets and a polyhedron with a new Cartesian product.

### Input

  * `cap`                   – lazy intersection of a Cartesian product array and                            a polyhedron
  * `CartesianProductArray` – target set type
  * `oa`                    – overapproximation option

### Output

A `CartesianProductArray` that overapproximates the intersection of `cpa` and `P`.

### Algorithm

The intersection only needs to be computed in the blocks of `cpa` that are constrained in `P`. Hence we first collect those constrained blocks in a lower-dimensional Cartesian product array and then convert to an `HPolytope` `X`. Then we take the intersection of `X` and the projection of `Y` onto the corresponding dimensions. (This projection is purely syntactic and exact.) Finally we decompose the result again and plug together the unaffected old blocks and the newly computed blocks. The result is a `CartesianProductArray` with the same block structure as in `X`.
