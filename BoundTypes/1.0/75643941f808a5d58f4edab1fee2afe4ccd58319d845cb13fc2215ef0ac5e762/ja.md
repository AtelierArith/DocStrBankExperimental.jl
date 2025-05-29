```
StringFixedLength{T<:AbstractString,V} <: BoundString{T}
StringFixedLength{T,V}(x::AbstractString)
```

値 `x` の型 `T` に対する文字列制約で、長さは `V` 文字と等しくなければなりません。

## 例

```jldoctest
julia> StringFixedLength{String,5}("abcde")
"abcde"

julia> StringFixedLength{String,5}("abc")
ERROR: ConstraintError: constraints of type StringFixedLength violated.
Wrong value: length of the "abc" must be equal to 5 characters (3).
[...]
```
