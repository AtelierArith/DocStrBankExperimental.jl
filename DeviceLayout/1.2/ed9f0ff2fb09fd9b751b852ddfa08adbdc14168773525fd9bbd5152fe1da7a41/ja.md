```
struct MeshSized{T, S} <: GeometryEntityStyle where {T, S <: Real}
    h::T
    α::S
end
```

スタイルは、SolidModelレンダリングで使用するメッシュサイズを持つGeometryEntityに注釈を付けます。生成されるメッシュには、次のように定義されたサイズフィールドが含まれます。

```
mesh size = `h` * max(`s_g`, (d/`h`)^`α`)
```

ここで、dはスタイル付きエンティティからの距離であり、`s_g`は`MeshingParameters`で指定されたグローバルメッシュスケールパラメータです。`h`の値が小さいほど、スタイル付きエンティティに付随するメッシュは細かくなり、`α`の値が大きいほど、スタイル付きエンティティからの距離に応じたサイズの増加が急速になります。

`α < 0`の場合、サイズフィールドはレンダリングに使用される`MeshingParameters`からの`α_default`を使用します。

また、[`meshsized_entity`](@ref)および[`SolidModels.MeshingParameters`](@ref)も参照してください。
