`Susceptibility` は、一般的なタイトバインディング `Model` に対する磁気応答 $χ^{ab}(Q , Ω)$ を表すデータ型です。

# 属性

  * `M       ::  Model`: 与えられたモデル。
  * `Qs      ::  Vector{Vector{Float64}}`: $χ^{ab}(Q , Ω)$ が計算される運動量点のセット。
  * `Omegas  ::  Vector{Float64}`: $χ^{ab}(Q , Ω)$ が計算されるエネルギーのセット。
  * `Spread  ::  Float64` : デルタ関数を合計する際の有限の広がり。
  * `chis    ::  Dict`: 異なる方向の $χ^{ab}(Q , Ω)$ を含む辞書、例えば `chis["xx"]` など。

この構造体を次のように初期化します。

```julia
Susceptibility(M::Model , Omegas::Vector{Float64} ;  eta::Float64 = 1e-2) = new{}(M, [], Omegas, eta, Dict())
Susceptibility(M::Model , Qs::Vector{Vector{Float64}}, Omegas::Vector{Float64} ;  eta::Float64 = 1e-2) = new{}(M, Qs, Omegas, eta, Dict())
```
