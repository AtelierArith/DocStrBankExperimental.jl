```
StringLowerCase{T<:AbstractString} <: BoundString{T}
StringLowerCase{T}(x::AbstractString)
```

値 `x` の型 `T` に対する文字列制約で、文字は小文字でなければなりません。

## 例

```jldoctest
julia> StringLowerCase{String}("abcdef")
"abcdef"

julia> StringLowerCase{String}("aBcdEf")
ERROR: ConstraintError: constraints of type StringLowerCase violated.
Wrong value: some characters of "aBcdEf" must be in lowercase (B,E).
[...]
```
