```
Renyi <: InformationMeasure
Renyi(q, base = 2)
Renyi(; q = 1.0, base = 2)
```

The Rényi generalized order-`q` entropy [Rényi1961](@cite), used with [`information`](@ref) to compute an entropy with units given by `base` (typically `2` or `MathConstants.e`).

## Description

Let $p$ be an array of probabilities (summing to 1). Then the Rényi generalized entropy is

$$
H_q(p) = \frac{1}{1-q} \log \left(\sum_i p[i]^q\right)
$$

and generalizes other known entropies, like e.g. the information entropy ($q = 1$, see [Shannon1948](@citet)), the maximum entropy ($q=0$, also known as Hartley entropy), or the correlation entropy ($q = 2$, also known as collision entropy).

The maximum value of the Rényi entropy is $\log_{base}(L)$, which is the entropy of the uniform distribution with $L$ the [`total_outcomes`](@ref).
