```
is_conditional_distribution( probabilities :: AbstractMatrix{<:Real}; atol=ATOL :: Flaot64 ) :: Bool
```

提供された行列が列確率的である場合に`true`を返します。つまり、各列が有効な確率分布であることを意味します。
