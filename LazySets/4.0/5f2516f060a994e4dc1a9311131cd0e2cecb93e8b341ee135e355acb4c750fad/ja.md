```
project(X::LazySet, block::AbstractVector{Int}, set_type::Type{<:LazySet},
        [n]::Int=dim(X); [kwargs...])
```

与えられたブロックとセットタイプにセットを投影し、過大評価を含む可能性があります。

### 入力

  * `X`        – セット
  * `block`    – ブロック構造 - 関心のある次元のベクトル
  * `set_type` – 目標セットタイプ
  * `n`        – （オプション、デフォルト: `dim(X)`）セット `X` の周囲の次元

### 出力

`set_type` のタイプのセットで、`X` の投影の過大評価を表します。

### アルゴリズム

1. ブロック座標系での単位行列 `M` を用いて、`M⋅X` でセット `X` を投影します。
2. `overapproximate` と `set_type` を使用して投影されたセットを過大評価します。
