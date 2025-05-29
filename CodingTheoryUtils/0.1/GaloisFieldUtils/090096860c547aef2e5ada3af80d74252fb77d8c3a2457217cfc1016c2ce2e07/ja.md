```
extract_degrees(polynomial::AbstractString) -> Vector{Int}
```

多項式の文字列表現から項の次数を抽出します。

多項式の文字列は「x^a + x^b + ... + 1」の形式である必要があります。項は「 + 」で区切られている必要があります。

# 例

julia> extract_degrees("x^3 + x + 1") 3-element Vector{Int64}:  3  1  0

julia> extract_degrees("x^5") 1-element Vector{Int64}:  5
