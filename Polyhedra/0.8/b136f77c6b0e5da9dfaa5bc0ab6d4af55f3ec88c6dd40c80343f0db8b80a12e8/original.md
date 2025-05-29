```
hchebyshevcenter(p::HRep[, solver]; linearity_detected=false, proper=true)
```

Return a tuple with the center and radius of the largest euclidean ball contained in the polyhedron `p`. Throws an error if the polyhedron is empty or if the radius is infinite. Linearity is detected first except if `linearity_detected`.

Note that a polytope may have several Chebyshev center. In general, the set of Chebyshev center of a polytope `p` is a polytope which has a lower dimension than `p` if `p` has a positive dimension. For instance, if `p` is the rectangle `[-2, 2] x [-1, 1]`, the Chebyshev radius of `p` is 1 and the set of Chebyshev centers is `[-1, 1] x {0}`. The *proper* Chebyshev center is `(0, 0)`, the Chebyshev center of `[-1, 1] x {0}`. If `!proper` then any Chebyshev center is returned (the one returned depends on the solver). Otherwise the proper Chebyshev center is computed. The proper Chebyshev center is defined by induction on the dimension of `p`. If `p` has dimension 0 then it is a singleton and its proper Chebyshev center   is the only element of `p`. Otherwise, the dimension of the set `q` of Chebyshev centers of `p` is smaller than the dimension of `p` and the proper Chebyshev center of `p` is the proper Chebyshev center of `q`.
