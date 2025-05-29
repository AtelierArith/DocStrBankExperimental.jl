```
string2coefvec(polynomial::AbstractString) -> Vector{Int}
```

多項式の文字列表現を係数ベクトル（Int）に変換します。多項式はGF(2)上にあると仮定されているため、係数は0または1です。ベクトルのインデックスは次数に対応し（インデックス1は次数0）、なります。

# 例

julia> string2coefvec("x^3 + x + 1") 4-element Vector{Int64}:  1  1  0  1

julia> string2coefvec("x^5") 6-element Vector{Int64}:  0  0  0  0  0  1 ```
