sortnatural(x::Vector{String}) => Vector(::String)

文字列ベクトルを自然順序でソートし、数値のソートを考慮します。

## 例

```julia
julia> myvec = ["12", "2", "1", "Y", "10", "X"];
julia> sort(myvec)
6-element Vector{String}:
 "1"
 "10"
 "12"
 "2"
 "X"
 "Y"
 julia> sortnatural(myvec)
 6-element Vector{String}:
  "1"
  "2"
  "10"
  "12"
  "X"
  "Y"
```
