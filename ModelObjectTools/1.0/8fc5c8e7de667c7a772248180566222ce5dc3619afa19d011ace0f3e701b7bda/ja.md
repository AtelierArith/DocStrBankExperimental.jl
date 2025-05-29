modelObjectFromAnother(base, pairs::Pair{Symbol,<:Any}...)

この関数を使用して、既存の構造体から新しい構造体を作成しますが、いくつかの指定された変更を除きます。

# 例

```julia-repl

julia> struct ExStr
       a::Float64
       vec::Tuple{Float64, Float64, Float64}
       end

julia> s = ExStr(3.0, (1.0,2.0,10.0))
ExStr(3.0, (1.0, 2.0, 10.0))

julia> s2 = modelObjectFromAnother(s, :vec => (2.0, 1.0, 5.0))
ExStr(3.0, (2.0, 1.0, 5.0))

julia> s3 = modelObjectFromAnother(s, :vec => (2.0, 1.0, 5.0), :a => 4.5)
ExStr(4.5, (2.0, 1.0, 5.0))
```
