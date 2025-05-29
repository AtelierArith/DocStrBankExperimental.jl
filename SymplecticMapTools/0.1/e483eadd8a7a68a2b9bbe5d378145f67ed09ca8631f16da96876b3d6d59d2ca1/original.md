```
birkhoff_extrapolation(h::Function, F::Function, x0::AbstractVector,
                       N::Integer, K::Integer; iterative::Bool=false,
                       x_prev::Union{AbstractArray,Nothing}=nothing,
                       rre::Bool=false)
```

As input, takes an initial point `x0`, a symplectic map `F`, and an observable `h` (can choose the identity as a default `h = (x)->x`). Then, the method

1. Computes a time series xs[:,n+1] = Fⁿ(x0)
2. Computes observable series hs[:,n] = h(xs[:,n])
3. Performs sequence extrapolation (RRE or MPE) on hs to obtain a model `c` of  length `2K+1` (with `K` unknowns), the extrapolated value applied to each  window, and a residual
4. Returns as `c, sums, resid, xs, hs[, history]` where `history` is a  diagnostic from the iterative solver that only returns when `iterative=true`

Use `x_prev` if you already know part of the sequence, but do not know the whole thing.
