三次元の場合のWeylノードをFukui-Hatsugai-Suzuki法に基づいて計算します [Fukui2005Chern](@cite)。

```
calcWeylNode(Hamiltonian::Function, n::Vector{Int64}; N::Int=51, gapless::Real=0.0, rounds::Bool=true)
```

引数

  * Hamiltionian::Function: 三次元の波数 `k` を引数とするハミルトニアン行列。
  * n::Vector{Int64}: Weylノードを計算する際の波数($2\pi\bm{n}/N$)。
  * N::Int=51: ブリルアンゾーンを離散化する際のメッシュ数。計算の精度を高めるために、`N`は奇数であることが望ましい。
  * gapless::Real: 状態が縮退するかどうかを決定する閾値。メッシュ(`N`)を粗くしつつ`gapless`を増やすことで、計算の精度が向上します。
  * rounds::Bool=true: トポロジカル数の値を整数値に丸めるオプション。`true`の場合、トポロジカル数は`Int`型の値を返し、`false`の場合は`Float`型の値を返します。
