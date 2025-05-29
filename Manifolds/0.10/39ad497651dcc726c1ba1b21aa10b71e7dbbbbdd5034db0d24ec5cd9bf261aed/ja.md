```
convert(::Type{AbstractMatrix}, p::SPDPoint)
```

点 `p` を行列として返します。行列は [`SPDPoint`](@ref) 内に格納されているか、`p.eigen` から再構築されます。
