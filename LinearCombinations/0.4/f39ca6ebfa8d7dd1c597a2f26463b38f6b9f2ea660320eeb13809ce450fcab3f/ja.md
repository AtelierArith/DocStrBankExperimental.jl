```
matrixrepr!(f, a::AbstractMatrix, b1::AbstractBasis, b0::AbstractBasis; iszero::Bool = false) -> a
```

線形写像 `f` を基底 `b0` (ソース) と `b1` (ターゲット) に関して表す行列を計算します。結果を `a` に格納し、`a` を返します。キーワード引数 `iszero` が `true` の場合、行列 `a` は最初にゼロで初期化されません。

詳細は [`matrixrepr`](@ref) を参照してください。
