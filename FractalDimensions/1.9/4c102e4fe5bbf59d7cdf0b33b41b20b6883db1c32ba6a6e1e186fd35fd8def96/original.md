```
higuchi_dim(x::AbstractVector [, ks])
```

Estimate the Higuchi dimension [Higuchi1988](@cite) of the graph of `x`.

## Description

The Higuchi dimension is a number `Δ ∈ [1, 2]` that quantifies the roughness of the graph of the function `x(t)`, assuming here that `x` is equi-sampled, like in the original paper.

The method estimates how the length of the graph increases as a function of the indices difference (which, in this context, is equivalent with differences in `t`). Specifically, we calculate the average length versus `k` as

$$
L_m(k) = \frac{N-1}{\lfloor \frac{N-m}{k} \rfloor k^2}
\sum_{i=1}^{\lfloor \frac{N-m}{k} \rfloor} |X_N(m+ik)-X_N(m+(i-1)k)| \\

L(k) = \frac{1}{k} \sum_{m=1}^k L_m(k)
$$

and then use [`linear_region`](@ref) in `-log2.(k)` vs `log2.(L)` as per usual when computing a fractal dimension.

The algorithm chooses default `ks` to be exponentially spaced in base-2, up to at most `2^8`. A user can provide their own `ks` as a second argument otherwise.

Use `FractalDimensions.higuchi_length(x, ks)` to obtain $L(k)$ directly.
