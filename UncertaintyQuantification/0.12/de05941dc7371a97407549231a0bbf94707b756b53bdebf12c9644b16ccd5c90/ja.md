```
ShinozukaDeodatis(ω::AbstractVector{<:Real}, σ::Real, b::Real)
```

指定されたパラメータを持つパワースペクトル密度関数を表す `ShinozukaDeodatis` インスタンスを構築します。

# 引数

  * `ω::AbstractVector{<:Real}`: 角周波数のベクトル。
  * `σ::Real`: 確率過程の分散に関連するハイパーパラメータ。
  * `b::Real`: 確率過程の相関長に関連するパラメータ。

# 戻り値

指定された引数（パラメータ）によって指定されたパワースペクトル密度関数を持つ離散化された `ShinozukaDeodatis` インスタンス。

# 例

```julia
w = 0:0.1:10
σ = 1.0
b = 0.5
sd = ShinozukaDeodatis(w, σ, b)
```
