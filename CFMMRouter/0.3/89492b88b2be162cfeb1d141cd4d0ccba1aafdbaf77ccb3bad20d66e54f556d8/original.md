```
UniV3(current_price, lower_ticks, liquidity, γ, Ai)
```

Creates a two coin Uniswap v3 CFMM. This CFMM is a collection of  [BoundedProduct](@ref) pools with disjoint price intervals. Prices refer to the amount of asset 2 per unit of asset 1. The `lower_ticks` vector stores the prices in decreasing order (i.e., asset 2 gets more expensive as the index increases). The `k+1`st price, where `k` is the number of pools, is assumed to be `Inf`. The `i`th entry of the `liquidity` vector stores the invariant of each pool  between price `p[i]` and `p[i+1]`. We use the square of the invariant in the paper, defined as

$$
\varphi(R) = (R_1 + \alpha)(R_2 + \beta).
$$

As before `γ` is the fee rate, and the `Ai` vector maps local to global indices.

For more, see An Eﬃcient Algorithm for Optimal Routing Through Constant  Function Market Makers.
