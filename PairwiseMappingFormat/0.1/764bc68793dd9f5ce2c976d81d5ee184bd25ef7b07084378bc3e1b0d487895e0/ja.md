```
query_coverage(rec::Record) -> Float64
```

アライメントによってカバーされるクエリの割合を計算します。

# 例

```jldoctest
julia> query_coverage(record)
0.9999535124653004
```

関連情報: [`target_coverage`](@ref), [`aln_identity`](@ref)
