```
allocate_packed(T, init, n) -> PackedVectorOfVectors
```

ネストされた要素型 `T` を持つパックされたベクトルのベクトルを割り当てます。`k` 番目のネストされたベクトルは長さ `nth(n,k)` になります。`init` の意味については `Vector{T}(init,n)` のドキュメントを参照してください。

# 例

```jldoctest
julia> allocate_packed(Ref{Int}, undef, [1,2,3])
3-element pack(::Vector{Vector{Ref{Int64}}}):
 [#undef]
 [#undef, #undef]
 [#undef, #undef, #undef]
```
