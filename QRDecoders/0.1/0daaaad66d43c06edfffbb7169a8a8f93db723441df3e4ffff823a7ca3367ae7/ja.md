```
qrdecode(mat::AbstractMatrix
        ; noerror::Bool=false
        , preferutf8::Bool=true
        , alg::ReedSolomonAlgorithm=Euclidean()
        )::QRInfo
```

QRコードデコーダー。

`noerror`が`true`の場合、デコーダーはQRコード`mat`がエラー訂正を必要とする際にException(ReedSolomonError/InfoError)を発生させます。

`preferutf8`が`true`の場合、デコーダーは`Byte`モードを扱う際に`UTF8`モードでメッセージをデコードしようとします。

エラー訂正アルゴリズムは変数`alg`によって指定されます（デフォルト: `Euclidean`）。
