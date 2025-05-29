```
NumberCustomBound{T<:Number,B} <: BoundNumber{T}
NumberCustomBound{T,B}(x::Number)
```

カスタム関数 `B` を使用して型 `T` の値 `x` に対する数値制約。関数 `B` はオブジェクト `x` のみを受け入れ、`true` または `false` を返す必要があります（またはカスタム [`ConstraintError`](@ref) をスローします）。

## 例

```julia-repl
julia> NumberCustomBound{Float64,x -> x % 2 == 0}(10.0)
10.0

julia> NumberCustomBound{Float64,x -> x % 2 == 0}(13.0)
ERROR: ConstraintError: constraints of type NumberCustomBound violated.
Wrong value: Custom constraint '#7' violated for value "13.0" of type Float64.
[...]
```
