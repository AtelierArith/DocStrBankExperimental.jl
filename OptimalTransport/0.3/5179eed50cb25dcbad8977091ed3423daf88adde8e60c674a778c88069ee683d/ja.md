```
sinkhorn2(
    μ, ν, C, ε, alg=SinkhornGibbs(); regularization=false, plan=nothing, kwargs...
)
```

ソースとターゲットの周辺分布 `μ` と `ν`、サイズ `(length(μ), length(ν))` のコスト行列 `C`、エントロピー正則化パラメータ `ε` を用いて、エントロピー的に正則化された最適輸送問題を解き、最適コストを返します。

事前に計算された最適輸送 `plan` を提供することができます。ここでサポートされている他のキーワード引数は、[`sinkhorn`](@ref) 関数と同じです。

!!! note
    Python Optimal Transport パッケージの `sinkhorn2` 関数と同様に、この関数は正則化項なしで最適輸送コストを返します。正則化項を含むコストは、`regularization=true` を設定することで計算できます。


関連情報: [`sinkhorn`](@ref)
