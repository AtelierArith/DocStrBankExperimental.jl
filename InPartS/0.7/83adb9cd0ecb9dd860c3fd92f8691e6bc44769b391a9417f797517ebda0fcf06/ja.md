```
SimpleParticleContainer{PT<:AbstractParticle}() <: AbstractParticleContainer
```

1つ以上の種の粒子を持つシミュレーションを処理し、開放境界および周期境界を持ちます。性能の良い時間発展のために、ドメインはサイズ `≥ interactionrange` のグリッドボックスに分割され、`InPartS.interactionrange` は新しい粒子タイプのために拡張する必要があり、`interactionrange` が相互作用する2つの粒子間の最大中心-中心距離以上であることを確認しなければなりません。
