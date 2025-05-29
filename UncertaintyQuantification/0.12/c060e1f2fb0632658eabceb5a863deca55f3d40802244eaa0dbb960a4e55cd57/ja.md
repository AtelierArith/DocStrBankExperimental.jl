```
KanaiTajimi(ω::AbstractVector{<:Real}, S_0::Real, ω_0::Real, ζ::Real) -> KanaiTajimi
```

与えられたパラメータを持つパワースペクトル密度関数を表す`KanaiTajimi`インスタンスを構築します。

# 引数

  * `ω::AbstractVector{<:Real}`: 角周波数のベクトル。
  * `S_0::Real`: スケーリングファクター。
  * `ω_0::Real`: 振動子の自然周波数。
  * `ζ::Real`: 振動子の減衰比。

# 戻り値

与えられた引数（パラメータ）によって指定された離散化された`KanaiTajimi`パワースペクトル密度関数。

# 例

```julia
w = 0:0.1:10
S_0 = 1.0
ω_0 = 2.0
ζ = 0.05
kt = KanaiTajimi(w, S_0, ω_0, ζ)
```
