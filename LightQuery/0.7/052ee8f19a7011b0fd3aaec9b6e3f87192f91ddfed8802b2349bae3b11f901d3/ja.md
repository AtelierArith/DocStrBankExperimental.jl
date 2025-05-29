```
order(unordered, key_function; keywords...)
```

一般化されたソート。`keywords` は `sort!` に渡されます。オプションについては、そちらのドキュメントを参照してください。オブジェクトがソートされていることを示すには [`By`](@ref) を使用してください。`key_function` の結果が型不安定な場合は、代わりに `hash ∘ key_function` を使用することを検討してください。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> collect(@inferred order([-2, 1], abs))
2-element Array{Int64,1}:
  1
 -2
```
