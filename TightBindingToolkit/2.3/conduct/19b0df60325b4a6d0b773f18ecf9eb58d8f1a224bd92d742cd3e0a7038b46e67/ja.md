`Conductivity`は、タイトバインディングモデルの電気伝導率を追跡するためのデータ型です。

# 属性

  * `M       ::  Model`: 伝導率を計算するタイトバインディングモデル。
  * `omegas  ::  Vector{Float64}`: DC伝導率を得るために積分するエネルギーの範囲。
  * `spread  ::  Float64`: 実周波数グリーン関数の乱れ/広がり。
  * `spectral::  Vector{Array{Matrix{ComplexF64}}}`: 指定された周波数およびすべての運動量点での行列スペクトル関数。
  * `sigma   ::  Dict{String, Float64}`: 異なる方向に沿った伝導率を含む辞書。

この構造体は次のように初期化します。

```julia
Conductivity(M::Model ; spread::Float64 = 1e-3)
Conductivity(M::Model , omegas::Vector{Float64} ; spread::Float64 = 1e-3)
```

充填または化学ポテンシャルを入力できます。特定の充填に対する対応するμ、または特定のμに対する充填は自動的に計算されます。
