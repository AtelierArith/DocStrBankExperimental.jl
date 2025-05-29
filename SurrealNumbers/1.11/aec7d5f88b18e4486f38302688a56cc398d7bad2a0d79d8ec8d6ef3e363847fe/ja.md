```
canonicalise(s::SurrealFinite)
```

サロエル数の形式をその同等の標準形に変換します。これは、有理数に変換してから再びサロエルに戻すことによって変換を行います。

## 例

```jldoctest
julia> convert(SurrealFinite, 1) - convert(SurrealFinite, 1)
{ { ϕ | { ϕ | ϕ } } | { { ϕ | ϕ } | ϕ } }
julia> pf( canonicalise( convert(SurrealFinite, 1) - convert(SurrealFinite, 1) ) )
{ ϕ | ϕ }
```
