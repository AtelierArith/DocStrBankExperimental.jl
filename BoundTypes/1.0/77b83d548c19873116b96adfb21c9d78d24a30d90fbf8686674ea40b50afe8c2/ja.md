```
StringCustomBound{T<:AbstractString,B} <: BoundString{T}
StringCustomBound{T,B}(x::AbstractString)
```

カスタム関数 `B` を使用して型 `T` の値 `x` に対する文字列制約。関数 `B` はオブジェクト `x` のみを受け入れ、`true` または `false` を返す必要があります（またはカスタム [`ConstraintError`](@ref) をスローします）。

## 例

```julia-repl
julia> StringCustomBound{String,x -> length(x) > 5}("abcdef")
"abcdef"

julia> StringCustomBound{String,x -> length(x) > 5}("abc")
ERROR: ConstraintError: constraints of type StringCustomBound violated.
Wrong value: Custom constraint '#5' violated for value "abc" of type String.
[...]
```
