```
rt_ports(Γ::Mesh, γ::Mesh ...)
```

`Γ`上にRT空間を構築し、`γ`の境界ペアに対して相対的です。`γ`は任意の数のポートペアを引数として受け入れ、タプル、配列、ベクトルなどを受け入れます。例えば、`rt_ports(Γ, a, b ...);` のように、a = [γ₁ γ₂]、b = (γ₃,γ₄) などです。ポートペアが供給されていない `rt_ports`、すなわち `rt_ports(Γ)` は `raviartthomas(Γ)` 関数に還元されます。RT空間は各ポートペアにおける電流の連続性を保証します。すなわち、メッシュΓからγ₁を通じて出て行く電流は、γ₂で考慮されます。

RT基底オブジェクトを返します。
