```
mass(particle::AbstractParticle)::Real
```

粒子のインターフェース関数。粒子の静止質量を返します（単位は電子質量）。

これは、各具体的な[`AbstractParticle`](@ref)のサブタイプに対して実装する必要があります。
