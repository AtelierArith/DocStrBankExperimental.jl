```
LayeredPositional <: AbstractPositional

LayeredPositional(layers::Positional...)
```

各セットに対して別々のルールを持つことができる[`Positional`](@ref)近傍のセット。

`LayeredPositional`の`neighbors`は、各近傍層のイテレータのタプルを返します。
