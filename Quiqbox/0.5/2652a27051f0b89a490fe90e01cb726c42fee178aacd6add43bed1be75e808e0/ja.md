```
markUnique(arr::AbstractArray{T}, args...; 
           compareFunction::Function=hasEqual, kws...) where {T} -> 
Tuple{Vector{Int}, Vector{T}}
```

`arr`内の要素をマークするインデックスの`Vector{Int}`を返します。同じ要素は同じインデックスでマークされ、すべてのユニークな要素を含む`Vector{T}`を返します。「ユニーク」（または「同じ」）の定義は、デフォルトで[`hasEqual`](@ref)に設定されている`compareFunction`に基づいています。`args`と`kws`は、それぞれ`compareFunction`の位置引数とキーワード引数のプレースホルダーです。

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
markUnique([1, [1, 2],"s", [1, 2]])

# 出力
([1, 2, 3, 2], Any[1, [1, 2], "s"])
```

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
begin
    struct S
        a::Int
        b::Float64
    end

    a = S(1, 2.0)
    b = S(1, 2.0)
    c = S(1, 2.1)
    d = a

    markUnique([a,b,c,d])
end

# 出力
([1, 1, 2, 1], S[S(1, 2.0), S(1, 2.1)])
```
