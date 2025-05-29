```
destructure!(vals, obj; offset = firstindex(vals) - 1) -> vals
```

オブジェクト `obj` を `vals[offset+1:offset+n]` に分解し、`vals` を返します。ここで `n = struct_length(obj)` は `obj` に格納されている値の総数です。

また、[`destructure`](@ref)、[`restructure`](@ref)、および [`struct_length`](@ref) も参照してください。
