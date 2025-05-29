```
AbstractOrbit
```

軌道を表します。特定の時点での惑星の位置、真異常、離心異常、または平均異常を計算するためのすべての情報を含んでいます。AbstractOrbitの異なる具体的な実装は、異なる量の情報を含んでいます。

軌道に関する基本情報は、`period(orbit)`のような関数を使用して照会できます。

軌道は、`orbitsolve(orb)`のような関数を使用して解決できます。

参照: `RadialVelocityOrbit`, `KepOrbit`, `VisualOrbit`
