```
is_identity(G::AbstractLieGroup, q; kwargs...)
```

`q`が[`AbstractLieGroup`](@ref) $\mathcal G$の単位元であるかどうかを確認します。これは、対応する[`AbstractGroupOperation`](@ref) `O`に対する[`Identity`](@ref)`{O}`であるか、（おおよそ）正しい点の表現であることを意味します。

# 参照

[`identity_element`](@ref), [`identity_element!`](@ref)
