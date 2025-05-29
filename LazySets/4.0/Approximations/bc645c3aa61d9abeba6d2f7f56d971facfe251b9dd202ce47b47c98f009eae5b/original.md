```
underapproximate(P::AbstractPolyhedron{N}, ::Type{Ellipsoid};
                 backend=default_sdp_solver(),
                 interior_point::AbstractVector{N}=chebyshev_center_radius(P)[1]
                ) where {N<:Real}
```

Underapproximate a polyhedral set by the maximum-volume ellipsoid.

### Input

  * `P`         – polyhedral set
  * `Ellipsoid` – type for dispatch
  * `backend`   – (optional, default: `default_sdp_solver()`) backend to solve                the semi-definite program
  * `interior_point` – (optional, default: `chebyshev_center_radius(P)[1]`) an                     interior point of the ellipsoid (needed for the algorithm:                     see below for details)

### Output

An ellipsoid $E$ such that $E ⊆ P$. $E$ has maximal volume if `P` is bounded (no such guarantee is given in directions where `P` is unbounded).

### Notes

The maximum-volume ellipsoid is also called *Löwner-John ellipsoid*.

The algorithm requires to specify a point in the interior of the ellipsoid which can be specified with the argument `interior_point`. If no such point is known (i.e., `interior_point == nothing`), the implementation will compute the Chebyshev center (see [`chebyshev_center_radius`](@ref)).

Note that the Chebyshev center will be computed using the default LP solver and not the passed SDP solver `backend` (because it is not guaranteed that `backend` supports LPs). If a custom LP solver should be used, the Chebyshev center needs to be computed and passed manually.

### Algorithm

We use the package [`SetProg.jl`](https://github.com/blegat/SetProg.jl/) to encode the problem directly.

An algorithm is described [here](https://systemanalysisdpt-cmc-msu.github.io/ellipsoids/doc/chap_ellcalc.html#maximum-volume-ellipsoids).
