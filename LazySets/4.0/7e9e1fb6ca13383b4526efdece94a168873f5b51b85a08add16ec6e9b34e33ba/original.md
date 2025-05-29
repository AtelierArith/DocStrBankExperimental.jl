```
chebyshev_center_radius(P::LazySet;
                        [backend]=default_polyhedra_backend(P),
                        [solver]=default_lp_solver_polyhedra(eltype(P); presolve=true))
```

Compute a [Chebyshev center](https://en.wikipedia.org/wiki/Chebyshev_center) and the corresponding radius of a polytopic set.

### Input

  * `P`       – polytopic set
  * `backend` – (optional; default: `default_polyhedra_backend(P)`) the backend              for polyhedral computations
  * `solver`  – (optional; default:              `default_lp_solver_polyhedra(N; presolve=true)`) the LP solver              passed to `Polyhedra`

### Output

The pair `(c, r)` where `c` is a Chebyshev center of `P` and `r` is the radius of the largest Euclidean ball with center `c` enclosed by `P`.

### Notes

The Chebyshev center is the center of a largest Euclidean ball enclosed by `P`. In general, the center of such a ball is not unique, but the radius is.

### Algorithm

We call `Polyhedra.chebyshevcenter`.
