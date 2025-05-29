```
CloughPenzien(ω::AbstractVector{<:Real}, S_0::Real, ω_f::Real, ζ_f::Real, ω_g::Real, ζ_g::Real)
```

与えられたパラメータを持つパワースペクトル密度関数を表す `CloughPenzien` インスタンスを構築します。

# 引数 / パラメータ

  * `ω::AbstractVector{<:Real}`: 角周波数のベクトル。
  * `S_0::Real`: スケーリング係数。
  * `ω_f::Real`: 最初のオシレーターの周波数パラメータ。
  * `ζ_f::Real`: 最初のオシレーターの減衰比。
  * `ω_g::Real`: 2番目のオシレーターの周波数パラメータ。
  * `ζ_g::Real`: 2番目のオシレーターの減衰比。

# 戻り値

与えられた引数（パラメータ）によって指定された離散化された `CloughPenzien` パワースペクトル密度関数。

# 例

```julia
w = 0:0.1:10
S_0 = 1.0
ω_f = 2.0
ζ_f = 0.05
ω_g = 3.0
ζ_g = 0.1
cp_psd = CloughPenzien(w, S_0, ω_f, ζ_f, ω_g, ζ_g)
```
