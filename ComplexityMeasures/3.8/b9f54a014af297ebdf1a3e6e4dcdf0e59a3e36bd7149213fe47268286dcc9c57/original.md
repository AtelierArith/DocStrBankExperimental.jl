```
BubbleEntropy <: ComplexityEstimator
BubbleEntropy(; m = 3, τ = 1, definition = Renyi(q = 2))
```

The `BubbleEntropy` complexity estimator [Manis2017](@cite) is just a difference between two entropies, each computed with the [`BubbleSortSwaps`](@ref) outcome space, for embedding dimensions `m + 1` and `m`, respectively. 

[Manis2017](@citet) use the [`Renyi`](@ref) entropy of order `q = 2` as the  information measure `definition`, but here you can use any [`InformationMeasure`](@ref). [Manis2017](@citet) formulates the "bubble entropy" as the normalized measure below,  while here you can also compute the unnormalized measure.

## Definition

For input data `x`, the "bubble entropy" is computed by first embedding the input data using embedding dimension `m` and embedding delay `τ` (call the embedded pts `y`), and  then computing the difference between the two entropies:

$$
BubbleEn_T(τ) = H_T(y, m + 1) - H_T(y, m)
$$

where $H_T(y, m)$ and $H_T(y, m + 1)$ are entropies of type $T$ (e.g. [`Renyi`](@ref)) computed with the input data `x` embedded to dimension $m$ and  $m+1$, respectively. Use [`complexity`](@ref) to compute this non-normalized version.  Use [`complexity_normalized`](@ref) to compute the normalized difference of entropies:

$$
BubbleEn_H(τ)^{norm} = 
\dfrac{H_T(x, m + 1) - H_T(x, m)}{max(H_T(x, m + 1)) - max(H_T(x, m))},
$$

where the maximum of the entropies for dimensions `m` and `m + 1` are computed using [`information_maximum`](@ref).

## Example

```julia
using ComplexityMeasures
x = rand(1000)
est = BubbleEntropy(m = 5, τ = 3)
complexity(est, x)
```
