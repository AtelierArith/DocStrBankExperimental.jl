```
StringMaxLength{T<:AbstractString,V} <: BoundString{T}
StringMaxLength{T,V}(x::AbstractString)
```

値 `x` の型 `T` に対する文字列制約で、長さは `V` 文字を超えてはなりません。

## 例

```jldoctest
julia> StringMaxLength{String,5}("abc")
"abc"

julia> StringMaxLength{String,5}("abcdef")
ERROR: ConstraintError: constraints of type StringMaxLength violated.
Wrong value: length of the "abcdef" must be no more than 5 characters (6).
[...]
```
