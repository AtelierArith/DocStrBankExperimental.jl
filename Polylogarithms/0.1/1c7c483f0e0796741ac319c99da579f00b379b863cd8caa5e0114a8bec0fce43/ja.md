複素数を解析します。

このコードは、すべての可能な複素数の形式を扱うわけではなく、Mathematicaによって出力される形式のみを扱います。

## 引数

  * `::Type{Complex{T}}`: 解析する型で、Tは実数型です
  * `s::AbstractString`: 解析する文字列

## 例

```jldoctest; setup = :(using Polylogarithms)
julia> parse( Complex{Float64}, "1.2 - 3.1*I")
1.2 + 3.1im
```
