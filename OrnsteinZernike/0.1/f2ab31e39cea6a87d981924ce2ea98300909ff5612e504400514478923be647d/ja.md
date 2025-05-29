```
SimpleLiquid{dims, ...} <: System
```

同次元、等方性の系に関する情報を保持し、放射対称のペア相互作用を持ちます。`dims`は次元数です。

次のように構築します。

`SimpleLiquid(dims, ρ, kBT, potential)`

フィールド:

  * ρ: 数密度。単一成分系の場合は`Number`でなければならず、混合系の場合は`Vector`でなければなりません。後者の場合、各要素はそれぞれの成分の数密度を含みます。
  * kBT: 熱エネルギー
  * potential::Potential: 相互作用ポテンシャル。

例:

```julia
ρ = 0.5; kBT = 1.1; dims = 3
pot = SingleComponentHardSpheres()
system = SimpleLiquid(dims, ρ, kBT, pot)
```

```julia
ρ = [0.5, 0.1]; kBT = 5.2; dims = 3
pot = MultiComponentHardSpheres([1.0, 0.8])
system = SimpleLiquid(dims, ρ, kBT, pot)
```
