```
fermionstates([T, ]Nmodes, Nparticles)
fermionstates([T, ]b, Nparticles)
```

N粒子のMモードに対するすべてのフェルミオン占有状態を生成します。`Nparticles`は、可変粒子数を持つヒルベルト空間を定義するためのベクトルであることができます。`T`は占有状態のタイプであり、デフォルトは`OccupationNumbers{FermionStatistics,Int}`ですが、任意の占有タイプを使用することができます。
