```
meshsized_entity(ent::GeometryEntity, h::T, α::S=-1.0) where {T, S <: Real}
```

[`MeshSized`](@ref) エンティティを作成し、SolidModel レンダリングで使用するメッシュサイズを指定します。生成されたメッシュには、次のように定義されたサイズフィールドが含まれます。

```
mesh size = `h` * max(`s_g`, (d/`h`)^`α`)
```

ここで、d はスタイル付きエンティティからの距離、`s_g` は `MeshingParameters` で指定されたグローバルメッシュスケールパラメータです。`h` の値が小さいほど、スタイル付きエンティティに付随するメッシュが細かくなり、`α` の値が大きいほど、スタイル付きエンティティからの距離に応じたサイズの急激な増加が得られます。

`α < 0` の場合、サイズフィールドはレンダリングに使用される [`SolidModels.MeshingParameters`](@ref) の `α_default` を使用します。
