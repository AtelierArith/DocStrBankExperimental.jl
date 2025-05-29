```
SurfaceTensionMorris(surface_tension_coefficient=1.0)
```

このモデルは、Morris [Morris2000](@cite) によって説明された表面張力アプローチを実装しています。これは、粒子の法線とその発散を使用して流体界面の曲率に基づいて表面張力を計算し、液滴形成や毛細管波動力学のような現象のシミュレーションに適しています。

詳細については、[`surface_tension`](@ref) を参照してください。

# キーワード

  * `surface_tension_coefficient=1.0`: 表面張力の力の大きさを調整し、シミュレーションにおける流体表面の挙動を調整可能にします。
