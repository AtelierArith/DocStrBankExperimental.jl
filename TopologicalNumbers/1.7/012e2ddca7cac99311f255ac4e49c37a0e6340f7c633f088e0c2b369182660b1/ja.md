```
calcChernSurface(H::Function, kn::String; kn_mesh::Int=51, N::Int=51, gapless::Real=0.0, rounds::Bool=true, plot::Bool=false)
```

引数

  * Hamiltionian::Function: 引数として三次元波数 `k` を持つハミルトニアン行列。
  * kn::String: ブリルアンゾーン内の `"kn"` 方向に垂直な平面のチェルン数を計算します（`"k1"`、`"k2"`、`"k3"`）。
  * kn_mesh::T: `"kn"` 方向のメッシュ数。
  * N::Int=51: ブリルアンゾーンを離散化する際のメッシュ数。計算の精度を高めるために、`N` は奇数であることが望ましいです。
  * gapless::Real: 状態が重複しているかどうかを決定する閾値。メッシュ（`N`）を粗くしつつ `gapless` を増やすことで、計算の精度が向上します。
  * rounds::Bool=true: トポロジカル数の値を整数値に丸めるオプション。`true` の場合、トポロジカル数は `Int` 型の値を返し、`false` の場合は `Float` 型の値を返します。
