```
StringMinLength{T<:AbstractString,V} <: BoundString{T}
StringMinLength{T,V}(x::AbstractString)
```

値 `x` の型 `T` に対する文字列制約で、長さは少なくとも `V` 文字でなければなりません。

## 例

```jldoctest
julia> StringMinLength{String,5}("abcdef")
"abcdef"

julia> StringMinLength{String,5}("abc")
ERROR: ConstraintError: constraints of type StringMinLength violated.
Wrong value: length of the "abc" must be at least 5 characters (3).
[...]
```
