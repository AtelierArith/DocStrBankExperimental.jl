```
second_virial_coefficient(model::EoSModel, T, z=SA[1.])
```

デフォルト単位: `[m^3]`

第二のビリアル係数 `B` を計算します。これは次のように定義されます：

```julia
B = lim(ρ->0)[∂Aᵣ/∂ρ]
```

ここで `Aᵣ` は残余ヘルムホルツエネルギーです。
