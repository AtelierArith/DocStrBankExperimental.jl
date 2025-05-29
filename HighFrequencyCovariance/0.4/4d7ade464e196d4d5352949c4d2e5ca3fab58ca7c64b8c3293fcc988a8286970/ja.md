```
preaveraging_end_returns(returns::Array{R,2}, m::Integer) where R<:Real
```

これは最初のいくつかと最後のいくつかのリターンを平均化します。私たちはこれを価格ではなくリターンに対して行います（BNHLS 2011で提案されています）。

## 参考文献

Barndorff-Nielsen, O., Hansen, P.R., Lunde, A., Shephard, N. 2011. - セクション 2.2.
