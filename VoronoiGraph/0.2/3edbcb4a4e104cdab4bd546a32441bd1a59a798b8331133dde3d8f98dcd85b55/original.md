```
mc_integrate(f::Function, i::Int, xs::Points, nmc=1000, nmc2=1000, searcher=Raycast(xs))
```

Integrate function `f` over cell `i` and its boundary using `nmc` rays per cell and `nmc2` points per ray for the volume integral.

# Returns:

  * `Vf::Real`: the volume integral of `f`
  * `Af::SparseVector`: Af[j] is the surface integral of `f` over the intersection between cells i and j.
  * `V::Real`: the volume of cell `i`
  * `A::SparseVector`: A[j] is the surface area of the intersection between cells i and j.
