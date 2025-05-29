```
zeemanshift(I::Ion, sublevel, B::Real)
```

`I`の`sublevel`の磁場`B`におけるゼーマンシフトを返します。`sublevel`にカスタムg因子が定義されている場合は、それが使用されます。そうでない場合は、`landegf`が使用されてランドé g因子を計算します。ゼーマンシフトは次のように計算されます：$ΔE = (μ_B/ħ) ⋅ g_f ⋅ B ⋅ m / 2π$
