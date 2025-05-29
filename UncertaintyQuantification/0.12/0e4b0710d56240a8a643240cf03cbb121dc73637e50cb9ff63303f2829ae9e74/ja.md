```
SpectralRepresentation(psd::AbstractPowerSpectralDensity, time::AbstractVector{<:Real}, name::Symbol) -> SpectralRepresentation
```

スペクトル表現法を使用して生成された確率過程を表す`SpectralRepresentation`インスタンスを構築します。

# 引数

  * `psd::AbstractPowerSpectralDensity`: パワースペクトル密度モデルのインスタンス。
  * `time::AbstractVector{<:Real}`: 時間点のベクトル。
  * `name::Symbol`: プロセスの名前を表すシンボル。

# 戻り値

与えられた引数（パラメータ）を持つ`SpectralRepresentation`インスタンス。

# 例

```julia
w = 0:0.1:10
S_0 = 1.0
ω_f = 2.0
ζ_f = 0.05
ω_g = 3.0
ζ_g = 0.1
psd = CloughPenzien(w, S_0, ω_f, ζ_f, ω_g, ζ_g)
t = 0:0.1:10
name = :process1
sr = SpectralRepresentation(psd, t, name)
```
