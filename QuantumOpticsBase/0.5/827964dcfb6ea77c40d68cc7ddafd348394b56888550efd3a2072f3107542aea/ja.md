```
bosonstates([T, ]Nmodes, Nparticles)
bosonstates([T, ]b, Nparticles)
```

NモードのN粒子のすべてのボソン占有状態を生成します。`Nparticles`は、可変粒子数を持つヒルベルト空間を定義するためのベクトルであることができます。`T`は占有状態のタイプであり、デフォルトは`OccupationNumbers{BosonStatistics,Int}`ですが、任意の占有タイプを使用することができます。
