```
hasIdentical(obj1, obj2, obj3...; 
             ignoreFunction::Bool=false, 
             ignoreContainer::Bool=false,
             decomposeNumberCollection::Bool=false) -> 
Bool
```

2つのコンテナ（例：`struct`）が同一であるかを比較します。 [`hasBoolRelation`](@ref) のインスタンス化です。

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
begin
    struct S
        a::Int
        b::Vector{Float64}
    end

    a = S(1, [1.0, 1.1])
    b = a
    c = b
    d = S(1, [1.0, 1.1])

    hasIdentical(a, b, c) |> println
    hasIdentical(a, b, c, d) |> println
end

# 出力
true
false
```
