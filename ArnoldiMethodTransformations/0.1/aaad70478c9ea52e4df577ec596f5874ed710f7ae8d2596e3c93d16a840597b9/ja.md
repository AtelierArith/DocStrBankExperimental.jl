```
module ArnoldiMethodTransformations
```

パッケージArnoldiMethodとのインターフェース用の便利なラッパーを提供します。

[こちら](https://haampie.github.io/ArnoldiMethod.jl/stable/)で詳述されているシフト・インバート変換を実装しています。

主な関数は `partialschur(A,[B],σ; kwargs...)` と `partialeigen(A,σ; kwargs...)` です。

定数 `USOLVER`、`PSOLVER`、および `MSOLVER` がエクスポートされています。
