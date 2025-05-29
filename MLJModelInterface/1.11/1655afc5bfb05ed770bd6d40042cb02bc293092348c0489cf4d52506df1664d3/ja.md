```
int(x)
```

`CategoricalString` または `CategoricalValue` `x` の位置整数であり、`x` のプールによって定義された順序に従います。`int(x)` の型は `x` の参照型です。

`x.ref` と混同しないでください。`x.ref` は `x` のプールの再順序付けによって変更されませんが、同じ型を持ちます。

```
int(X::CategoricalArray)
int(W::Array{<:CategoricalString})
int(W::Array{<:CategoricalValue})
```

`int` のブロードキャスト版。

```julia-repl
julia> v = categorical(["c", "b", "c", "a"])
4-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "c"
 "b"
 "c"
 "a"

julia> levels(v)
3-element Vector{String}:
 "a"
 "b"
 "c"

julia> int(v)
4-element Vector{UInt32}:
 0x00000003
 0x00000002
 0x00000003
 0x00000001
```

参照: [`decoder`](@ref).
