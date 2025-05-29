```
evaluate(sr::SpectralRepresentation, ϕ::AbstractVector{<:Real}) -> AbstractVector{<:Real}
```

指定された `SpectralRepresentation` インスタンスとランダム位相角のベクトルに対して確率過程を評価します。

# 引数

  * `sr::SpectralRepresentation`: `SpectralRepresentation` 構造体のインスタンス。
  * `ϕ::AbstractVector{<:Real}`: ランダム位相角のベクトル。

# 戻り値

評価された確率過程を表す実数のベクトル。

# 例

```julia
w = 0:0.1:10
psd = CloughPenzien(w, 1.0, 2.0, 0.05, 3.0, 0.1)
t = 0:0.1:10
name = :process1
sr = SpectralRepresentation(psd, t, name)
ϕ = rand(Uniform(0, 2π), length(psd.ω))
process_values = evaluate(sr, ϕ)
```
