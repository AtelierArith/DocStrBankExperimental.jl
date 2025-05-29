```
decoded_size_range(e)::StepRange{Int64, Int64}
```

エンコーディングのための許可された `src` サイズの範囲を返します。

返された範囲内の任意の値に対する [`encode_bound`](@ref) は `0:typemax(Int64)-1` にある必要があります。

詳細は [`encode_bound`](@ref) を参照してください。
