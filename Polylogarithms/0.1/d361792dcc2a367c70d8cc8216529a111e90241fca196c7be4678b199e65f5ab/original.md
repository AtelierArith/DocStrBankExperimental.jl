Parse rational numbers.

```
From https://github.com/JuliaLang/julia/issues/18328
```

## Arguments

  * `::Type{Rational{T}}`: the type to parse to, where T is an Integer number type
  * `s::AbstractString`: the string to parse

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> parse( Rational{Int64}, "1 / 2")
1//2
```
