```julia
is_anti_particle(_::QEDbase.AbstractParticle) -> Bool

```

粒子のインターフェース関数。渡された[`AbstractParticle`](@ref)のサブタイプがその粒子の対称物として*反粒子*と見なすことができる場合は`true`を返し、それ以外の場合は`false`を返します。すべての[`AbstractParticle`](@ref)のサブタイプに対する`is_anti_particle`のデフォルト実装は常に`false`を返します。
