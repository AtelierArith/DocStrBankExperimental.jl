```
tokenize(::Type{E}, data, version=1) -> Tokenizer
```

`Tokenizer{E, typeof(data), version}`を作成し、`data`上で型`E`のトークンを反復処理します。

参照: [`Tokenizer`](@ref), [`make_tokenizer`](@ref), [`compile`](@ref)

# 例

```jldoctest
julia> tokenize(UInt32, "hello")
Tokenizer{UInt32, String, 1}("hello")

julia> tokenize(Int8, [1, 2, 3], 3)
Tokenizer{Int8, Vector{Int64}, 3}([1, 2, 3])
```
