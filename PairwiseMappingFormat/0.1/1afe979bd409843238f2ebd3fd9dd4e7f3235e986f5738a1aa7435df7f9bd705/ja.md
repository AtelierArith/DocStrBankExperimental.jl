```
target_coverage(rec::Record) -> Float64
```

アライメントによってカバーされるターゲットの割合を計算します。

# 例

```jldoctest
julia> target_coverage(record)
0.044934629307437725
```

関連情報: [`query_coverage`](@ref), [`aln_identity`](@ref)
