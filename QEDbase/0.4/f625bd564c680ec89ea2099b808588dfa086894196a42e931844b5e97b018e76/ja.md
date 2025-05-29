```julia
is_particle(_::QEDbase.AbstractParticle) -> Bool

```

粒子のインターフェース関数。渡された[`AbstractParticle`](@ref)のサブタイプが反粒子とは異なる*粒子*と見なすことができる場合は`true`を返し、それ以外の場合は`false`を返します。すべての[`AbstractParticle`](@ref)のサブタイプに対する`is_particle`のデフォルト実装は常に`true`を返します。
