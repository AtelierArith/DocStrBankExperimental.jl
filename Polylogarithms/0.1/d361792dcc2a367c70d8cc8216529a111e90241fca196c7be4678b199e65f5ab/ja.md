有理数を解析します。

```
From https://github.com/JuliaLang/julia/issues/18328
```

## 引数

  * `::Type{Rational{T}}`: 解析する型で、Tは整数型です
  * `s::AbstractString`: 解析する文字列

## 例

```jldoctest; setup = :(using Polylogarithms)
julia> parse( Rational{Int64}, "1 / 2")
1//2
```
