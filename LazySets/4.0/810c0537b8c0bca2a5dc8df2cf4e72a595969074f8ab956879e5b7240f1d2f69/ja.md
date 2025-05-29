```
project(X::LazySet, block::AbstractVector{Int}, [::Nothing=nothing],
        [n]::Int=dim(X); [kwargs...])
```

与えられたブロックにセットを投影するために、具体的な線形マップを使用します。

### 入力

  * `X`       – セット
  * `block`   – ブロック構造 - 関心のある次元を持つベクトル
  * `nothing` – (デフォルト: `nothing`) ディスパッチに必要
  * `n`       – (オプション、デフォルト: `dim(X)`) セット `X` の周囲の次元

### 出力

ブロック `block` への `X` の投影を表すセット。

### アルゴリズム

関数 `linear_map` を適用します。
