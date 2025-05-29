```
uniformranking(μ)
```

Returns a (μ, λ)-uniform ranking selection function, see [Selection Interface](@ref) with the best individuals parameter `μ`.

In uniform ranking, the best $\mu$ individuals are assigned a selection probability of $1/\mu$ while the rest them are discarded [^2].
