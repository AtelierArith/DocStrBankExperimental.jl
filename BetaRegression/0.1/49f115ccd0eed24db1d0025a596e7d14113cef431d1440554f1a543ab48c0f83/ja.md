```
BetaRegressionModel(X, y, link=LogitLink(), precisionlink=IdentityLink();
                    weights=nothing, offset=nothing)
```

与えられたモデル行列 `X`、応答 `y`、平均リンク関数 `link`、精度リンク関数 `precisionlink`、およびオプションで `weights` と `offset` を使用して `BetaRegressionModel` オブジェクトを構築します。返されるオブジェクトは、`fit!` が呼び出されるまでフィットされていないことに注意してください。

!!! warning
    ユーザー提供の重みのサポートは現在不完全です; `nothing` または空の配列以外の値を `weights` に渡すと、現在エラーが発生します。

