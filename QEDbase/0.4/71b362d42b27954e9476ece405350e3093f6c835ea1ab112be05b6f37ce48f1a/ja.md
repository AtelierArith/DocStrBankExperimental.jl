```
AbstractParticleType <: AbstractParticle
```

これはすべての粒子種のための抽象基本型です。`AbstractParticleType`のサブタイプに定義されたすべての機能は静的であるべきであり、すなわちコンパイル時に知られている必要があります。粒子に四運動量や粒子状態などのランタイム情報を追加する場合は、代わりに[`AbstractParticle`](@ref)の具体的なサブタイプを実装することを検討してください。これには型パラメータ`P<:AbstractParticleType`が含まれる場合があります。

`AbstractParticleType`の具体的な組み込みサブタイプは`QEDcore.jl`で利用可能であり、常にシングルトンであるべきです。
