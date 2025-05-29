```julia
is_fermion(_::QEDbase.AbstractParticle) -> Bool

```

粒子のインターフェース関数。渡された[`AbstractParticle`](@ref)のサブタイプが粒子統計の意味で*フェルミオン*と見なせる場合は`true`を返し、それ以外の場合は`false`を返します。すべての[`AbstractParticle`](@ref)のサブタイプに対する`is_fermion`のデフォルト実装は常に`false`を返します。
