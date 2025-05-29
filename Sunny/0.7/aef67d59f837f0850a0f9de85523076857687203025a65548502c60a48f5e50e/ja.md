```
reshape_supercell(sys::System, shape)
```

既存の[`System`](@ref)を、要求されたスーパーセルの形状と周期性を持つ新しいものにマッピングします。$3×3$の整数行列`shape`の列は、元の結晶格子ベクトルの単位で測定されたスーパーセル格子ベクトルを表します。相互作用、スピン、およびその他の設定は`sys`から継承されます。

`shape`が対角行列である特別な場合、この関数は[`resize_supercell`](@ref)と一致します。

他に[`repeat_periodically`](@ref)も参照してください。
