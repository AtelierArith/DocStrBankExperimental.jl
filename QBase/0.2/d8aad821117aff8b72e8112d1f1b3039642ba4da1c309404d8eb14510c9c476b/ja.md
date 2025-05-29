```
is_kraus_channel(
    kraus_ops :: Vector{<:AbstractMatrix};
    atol=ATOL :: Float64
) :: Bool
```

`kraus_ops`が量子チャネルを構成する場合は`true`を返します。要件は次のとおりです：

  * 完全性、$\sum_{i} K^{\dagger}_i K_i = \mathbb{I}$。
