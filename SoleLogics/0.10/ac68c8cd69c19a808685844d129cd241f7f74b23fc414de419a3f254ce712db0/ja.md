```
truthtype(::Type{<:AbstractAlgebra{T}}) where {T<:Truth} = T
truthtype(a::AbstractAlgebra) = truthtype(typeof(a))
```

代数の真理値を表すためのJulia型です。

関連情報は[`AbstractAlgebra`](@ref)を参照してください。
