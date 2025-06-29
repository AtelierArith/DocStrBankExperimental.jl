```
v = InnerProductVec(vec, dotf)
```

Create a new vector `v` from an existing vector `dotf` with a modified inner product given by `inner`. The vector `vec`, which can be any type (not necessarily `Vector`) that supports the basic vector interface required by KrylovKit, is wrapped in a custom struct `v::InnerProductVec`. All vector space functionality such as addition and multiplication with scalars (both out of place and in place using `mul!`, `rmul!`, `axpy!` and `axpby!`) applied to `v` is simply forwarded to `v.vec`. The inner product between vectors `v1 = InnerProductVec(vec1, dotf)` and `v2 = InnerProductVec(vec2, dotf)` is computed as `dot(v1, v2) = dotf(v1.vec, v2.vec) = dotf(vec1, vec2)`. The inner product between vectors with different `dotf` functions is not defined. Similarly, The norm of `v::InnerProductVec` is defined as `v = sqrt(real(dot(v, v))) = sqrt(real(dotf(vec, vec)))`.

In a (linear) map applied to `v`, the original vector can be obtained as `v.vec` or simply as `v[]`.
