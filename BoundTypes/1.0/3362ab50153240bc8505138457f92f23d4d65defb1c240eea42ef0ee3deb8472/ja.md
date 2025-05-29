```
StringUpperCase{T<:AbstractString} <: BoundString{T}
StringUpperCase{T}(x::AbstractString)
```

値 `x` の型 `T` に対する文字列制約で、文字はすべて大文字でなければなりません。

## 例

```jldoctest
julia> StringUpperCase{String}("ABCDEF")
"ABCDEF"

julia> StringUpperCase{String}("AbCDeF")
ERROR: ConstraintError: constraints of type StringUpperCase violated.
Wrong value: some characters of "AbCDeF" must be in uppercase (b,e).
[...]
```
