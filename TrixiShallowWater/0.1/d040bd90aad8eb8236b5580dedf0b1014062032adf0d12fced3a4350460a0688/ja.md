```
ManningFriction(; n)
```

マンニング摩擦モデルを作成します。これはマンニング係数 `n` を用いた底部摩擦のモデルです。この型は、`shear_stress` を計算する際にそれぞれの摩擦法則に基づいて `shear_stress_coefficient` を通じてディスパッチするために使用されます。
