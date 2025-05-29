```
energy_map(Xw, y, method)
```

分解された入力信号 `Xw` と対応するラベル `y` に基づいてエネルギーマップを計算します。

# 引数

  * `Xw::AbstractArray{S} where S<:AbstractFloat`: 分解された1Dまたは2D信号。
  * `y::AbstractVector{T} where T`: `Xw` の信号に対応するラベル。
  * `method::EnergyMap`: 計算するエネルギーマップのタイプ。サポートされているタイプは次のとおりです：

      * `TimeFrequency()`
      * `ProbabilityDensity()`
      * `Signatures()`

# 戻り値

  * `Γ`: 計算されたエネルギーマップ。入力 `method` に応じて、`Γ` のデータ構造は次のようになります：

      * `TimeFrequency()` $\Longrightarrow$ `Array{S,3}`（1D信号の場合）または `Array{S,4}`（2D信号の場合）。
      * `ProbabilityDensity()` $\Longrightarrow$ `Array{S,4}`（1D信号の場合）または `Array{S,5}`（2D信号の場合）。
      * `Signatures(weight = :equal)`: $\Longrightarrow$ Vector{NamedTuple{(:coef, :weight), Tuple{Array{S}, S}}}
      * `Signatures(weight = :pdf`: $\Longrightarrow$ Vector{NamedTuple{(:coef, :weight), Tuple{Array{S}, Array{S}}}}

!!! tip
    どのタイプの重みでも `method = Signatures()` を設定すると、出力は名前付きタプルのベクトルになります。各名前付きタプルには、同じラベルのすべての信号の係数と重みが含まれています。


# 例

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
Xw = wpdall(X, wavelet(WT.haar))

energy_map(Xw, y, TimeFrequency())
energy_map(Xw, y, ProbabilityDensity())
energy_map(Xw, y, Signatures())
```

**参照:** [`EnergyMap`](@ref). [`TimeFrequency`](@ref), [`ProbabilityDensity`](@ref)
