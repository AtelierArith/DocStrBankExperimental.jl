```
is_point(G::AbstractLieGroup, g; kwargs...)
```

`g`がLie群`G`の有効な点であるかどうかを確認します。これは、`g`が[`base_manifold`](@ref)`G`の有効な点であるかどうかを確認することにフォールバックします。ただし、`g`が[`Identity`](@ref)である場合は、`G`に対応する単位元であるかどうかが確認されます。
