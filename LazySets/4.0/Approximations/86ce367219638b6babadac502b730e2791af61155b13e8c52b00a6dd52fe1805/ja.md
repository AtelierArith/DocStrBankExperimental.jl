```
project(S::LazySet,
        block::AbstractVector{Int},
        directions::Type{<:AbstractDirections},
        [n]::Int;
        [kwargs...]
       )
```

高次元集合を与えられたブロックに方向ベクトルを使用して射影します。

### 入力

  * `S`          – 集合
  * `block`      – ブロック構造 - 興味のある次元を持つベクトル
  * `directions` – 方向ベクトル
  * `n`          – （オプション、デフォルト: `dim(S)`）集合 `S` の周囲の次元

### 出力

与えられた方向における `S` の射影の多面体の過大評価。
