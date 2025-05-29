```julia
FourierSkOp(m, d, k; dithering, kwargs...)

```

A sketching operator which computes a linear sketch of random Fourier features, i.e. $s(X) = mean(Φ(xᵢ))$ with $Φ(x) = exp.(i Ωᵀx)$. Here $Ω$ is a (randomly drawn) matrix whose columns can be interpreted as frequency vectors, whose distribution depends on the kernel `k`.
