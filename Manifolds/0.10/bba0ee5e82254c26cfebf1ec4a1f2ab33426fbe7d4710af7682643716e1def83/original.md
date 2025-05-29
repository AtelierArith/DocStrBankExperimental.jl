```
inner(M::Tucker, p::TuckerPoint, X::TuckerTangentVector, Y::TuckerTangentVector)
```

The Euclidean inner product between tangent vectors `X` and `X` at the point `p` on the Tucker manifold. This is equal to `embed(M, p, X) ⋅ embed(M, p, Y)`.

```
inner(::Tucker, A::TuckerPoint, X::TuckerTangentVector, Y)
inner(::Tucker, A::TuckerPoint, X, Y::TuckerTangentVector)
```

The Euclidean inner product between `X` and `Y` where `X` is a vector tangent to the Tucker manifold at `p` and `Y` is a vector in the ambient space or vice versa. The vector in the ambient space is represented as a full tensor, i.e., a multidimensional array.
