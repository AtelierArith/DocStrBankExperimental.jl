```
project(S::LazySet, block::AbstractVector{Int}, set_type::Type{<:LinearMap},
        [n]::Int=dim(S); [kwargs...])
```

高次元集合を指定されたブロックに射影するために、遅延線形写像を使用します。

### 入力

  * `S`         – 集合
  * `block`     – ブロック構造 - 関心のある次元のベクトル
  * `LinearMap` – ディスパッチに使用
  * `n`         – （オプション、デフォルト: `dim(S)`）集合 `S` の周囲の次元

### 出力

集合 `S` をブロック `block` に射影する遅延 `LinearMap`。
