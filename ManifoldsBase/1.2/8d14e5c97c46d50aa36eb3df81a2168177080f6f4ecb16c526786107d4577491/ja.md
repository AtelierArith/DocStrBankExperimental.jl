```
get_embedding(M::AbstractDecoratorManifold)
get_embedding(M::AbstractDecoratorManifold, p)
```

抽象デコレーターを持つ多様体の埋め込みを指定します。埋め込みは点の表現に依存する可能性があり、異なる点の表現は[`AbstractManifoldPoint`](@ref)のサブタイプとして区別されます。一意またはデフォルトの表現は、単に`AbstractArray`である可能性もあります。
