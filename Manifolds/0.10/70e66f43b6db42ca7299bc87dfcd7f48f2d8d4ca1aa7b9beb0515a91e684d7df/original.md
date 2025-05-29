```
inner(M::Circle, p, X, Y)
```

Compute the inner product of the two tangent vectors `X,Y` from the tangent plane at `p` on the [`Circle`](@ref) `M` using the restriction of the metric from the embedding, i.e.

$$
g_p(X,Y) = X*Y
$$

for the real case and

$$
g_p(X,Y) = Y^\mathrm{T}X
$$

for the complex case interpreting complex numbers in the Gaussian plane.
