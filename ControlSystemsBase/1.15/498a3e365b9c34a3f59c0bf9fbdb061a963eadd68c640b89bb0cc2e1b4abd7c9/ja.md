```
tzeros(sys)
tzeros(sys::AbstractStateSpace; extra=Val(false))
```

システム `sys` の不変ゼロを計算します。`sys` が最小実現の場合、これらは伝送ゼロでもあります。

`sys` が状態空間システムの場合、関数には追加のキーワード引数があります。詳細については [`?ControlSystemsBase.MatrixPencils.spzeros`](https://andreasvarga.github.io/MatrixPencils.jl/dev/sklfapps.html#MatrixPencils.spzeros) を参照してください。`extra = Val(true)` の場合、関数は `z, iz, KRInfo` を返します。ここで `z` は伝送ゼロ、`iz` の無限ゼロの重複度に関する情報、KRInfo オブジェクトのクロンカー構造に関する情報です。無限ゼロの数は `iz` の成分の合計です。

`BigFloat` のような非 BLAS 浮動小数点数を持つシステムのゼロを計算するには、`tzeros` を呼び出す前に `GenericSchur.jl` パッケージをインストールしてロードしてください。
