```
discriminant_measure(Γ, dm)
```

エネルギーマップから計算された各部分空間の判別測度を計算します。

# 引数

  * `Γ`: `energy_map` 関数から計算されたエネルギーマップ。`Γ` のデータ構造は、対応するエネルギーマップに応じて次のようになります：

      * `TimeFrequency()`: 1D信号の場合は `AbstractArray{T,3}`、2D信号の場合は `AbstractArray{T,4}`。
      * `ProbabilityDensity()`: 1D信号の場合は `AbstractArray{T,4}`、2D信号の場合は `AbstractArray{T,5}`。
      * `Signatures()`: `AbstractVector{NamedTuple{(:coef, :weight), Tuple{S₁,S₂}}}`。
  * `dm::DiscriminantMeasure`: 判別測度のタイプ。`dm` のタイプは `Γ` のタイプと一致する必要があります。

# 戻り値

  * `D::Array{T}`: 分解された信号の各係数における判別測度。

# 例

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
Xw = wpdall(X, wavelet(WT.haar))

Γ = energy_map(Xw, y, TimeFrequency()); discriminant_measure(Γ, AsymmetricRelativeEntropy())
Γ = energy_map(Xw, y, ProbabilityDensity()); discriminant_measure(Γ, LpDistance())
Γ = energy_map(Xw, y, Signatures()); discriminant_measure(Γ, EarthMoverDistance())
```

**参照:** [`pairwise_discriminant_measure`](@ref)
