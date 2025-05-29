```julia
ThermalWindPotentialVorticity(model; tracer, location)

```

熱風ポテンシャル渦度を計算します。これは、`model`の熱風バランスを仮定し、コリオリ回転の特性は`model.coriolis`から取得されます。この場合のポテンシャル渦度は次のように定義されます。

```
    TWPV = (f + ωᶻ) ∂b/∂z - f ((∂U/∂z)² + (∂V/∂z)²)
```

ここで、`f`はコリオリ周波数、`ωᶻ`は`z`方向の相対渦度、`b`は浮力、`∂U/∂z`および`∂V/∂z`は熱風せん断を構成します。
