```
StringPattern{T<:AbstractString,P} <: BoundString{T}
StringPattern{T,P}(x::AbstractString)
```

値 `x` の型 `T` に対する文字列制約で、正規表現パターン `P` に一致する必要があります。

!!! note
    正規表現を渡すにはヘルパー関数 [`@pattern_str`](@ref) を使用してください。


## 例

```jldoctest
julia> StringPattern{String,pattern"^[a-zA-Z0-9_]+$"}("abcde")
"abcde"

julia> StringPattern{String,pattern"^[a-zA-Z0-9_]+$"}("abc+def")
ERROR: ConstraintError: constraints of type StringPattern violated.
Wrong value: "abc+def" must match to regex pattern /^[a-zA-Z0-9_]+$/.
[...]
```
