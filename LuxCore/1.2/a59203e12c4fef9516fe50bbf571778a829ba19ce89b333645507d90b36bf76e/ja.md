```
abstract type AbstractLuxContainerLayer{layers} <: AbstractLuxLayer
```

特定のLuxレイヤーのための抽象コンテナタイプです。`layers`はレイヤーのフィールド名を含むタプルであり、それを使用してパラメータと状態を構築します。

カスタムレイヤーを実装するユーザーは、[`AbstractLuxLayer`](@ref)と同じ関数を拡張できます。

!!! tip "高度な構造操作"
    これらのレイヤーの構築後の高度な構造操作は、`Functors.fmap`を介して可能です。より柔軟なインターフェースを希望する場合は、`Lux.Experimental.@layer_map`の使用をお勧めします。


!!! note "`fmap` サポート"
    `fmap`サポートは、`Functors.jl`と`Setfield.jl`をロードすることで明示的に有効にする必要があります。


!!! warning "1.0以前の動作からの変更"
    以前は、`layers`がシングルトンタプルである場合、[`initialparameters`](@ref)および[`initialstates`](@ref)は単一フィールド`layers`のパラメータと状態を返していました。`v1.0.0`以降、シングルトンタプルの場合でも、パラメータ/状態はフィールドと同じ名前の`NamedTuple`にラップされます。シングルトンタプルの以前の動作を再現するには、[`AbstractLuxWrapperLayer`](@ref)を参照してください。

