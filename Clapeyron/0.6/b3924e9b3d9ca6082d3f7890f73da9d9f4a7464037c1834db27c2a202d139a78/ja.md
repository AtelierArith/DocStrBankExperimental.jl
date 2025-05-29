```
cross_second_virial(model,T,z)
```

デフォルト単位: `[m^3]`

バイナリ混合物の第二交差ビリアル係数 (B₁₂) を定義に基づいて計算します:

```julia
B̄ = x₁^2*B₁₁ + 2x₁x₂B₁₂ + x₂^2*B₂₂
B₁₂ = (B̄ - x₁^2*B₁₁ - x₂^2*B₂₂)/2x₁x₂
```

!!! info "組成依存特性"
    状態方程式から計算された第二交差ビリアル係数は、組成に依存する可能性があります [1] が、通常、第二ビリアル係数を得るための実験は、2つの気体の同じ体積を混合することによって行われます。この方法でB12を計算するには、(Clapeyron.equivol*cross*second_virial)[@ref] を使用できます。


## 参考文献

1. Jäger, A., Breitkopf, C., & Richter, M. (2021). The representation of cross second virial coefficients by multifluid mixture models and other equations of state. Industrial & Engineering Chemistry Research, 60(25), 9286–9295. [doi:10.1021/acs.iecr.1c01186](https://doi.org/10.1021/acs.iecr.1c01186)
