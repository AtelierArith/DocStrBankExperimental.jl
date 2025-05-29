```
histvar!(out::AbstractArray{TF,3}, irfs::AbstractArray{TF,3}, shocks::AbstractMatrix)
```

インパルス応答係数 `irfs` と歴史的 `shocks` に基づいて、歴史的分解に使用される分散を計算します。結果は配列 `out` に格納されます。詳細は [`histvar`](@ref) を参照してください。
