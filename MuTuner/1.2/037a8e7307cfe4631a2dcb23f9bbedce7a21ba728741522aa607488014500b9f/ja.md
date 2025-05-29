```
MuTunerLogger(n₀::T, β::T, V::Int, u₀::T=1.0, μ₀::T=0.0, c::T=0.5,
              s::S=zero(T)) where {T<:AbstractFloat, S<:Number}
```

[`MuTunerLogger`](@ref) のインスタンスを構築します。

# 引数

  * `n₀::T`: 目標粒子密度 $\langle n \rangle$。
  * `β::T`: 逆温度。
  * `V::Int`: 系のサイズ。
  * `u₀::T=1.0`: 特徴的な強度エネルギースケール。
  * `μ₀::T=0.0`: 化学ポテンシャルの初期推定。
  * `c::T=0.5`: 忘却平均と分散を計算する際に破棄する履歴の割合。
  * `s::S=zero(T)`: 符号の例で、符号の型が実数か複素数かを判断します。
