```
aln_identity(rec::Record) -> Float64
```

ヌクレオチド/残基のアイデンティティを返します。これは、一致の数をアライメントの長さで割ったものとして定義されます。これは0から1の間の数です。

# 例

```jldoctest
julia> aln_identity(record)
1.0
```

関連情報: [`query_coverage`](@ref), [`target_coverage`](@ref)
