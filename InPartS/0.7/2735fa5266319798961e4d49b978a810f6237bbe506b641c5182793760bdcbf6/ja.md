```
ParticlesObstacleContainer{PT <: AbstractParticle, SO}() <: AbstractParticleContainer
```

粒子と壁のような障害物の両方を含むシミュレーションに適したハンドラーです。粒子のロジックは `SimpleParticleContainer` のそれと同じです。障害物として渡されるオブジェクトは静的です。動くことはできませんが、任意のサイズを持つことができます。効率的な時間発展を可能にするために、障害物は相互作用に関連するグリッドボックスの事前計算を可能にする `InPartS.interactionpolygon` を実装する必要があります。
