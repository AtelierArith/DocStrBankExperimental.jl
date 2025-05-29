```
ordinary_variable(x::Union{AbstractVariable, AbstractVector{<:AbstractVariable}})
```

与えられた（複素値の）変数が共役、実部、または虚部を取ることによって変換された場合、ユーザーによって定義された元の変数を返します。

参照してください [`conj`](@ref), [`real`](@ref), [`imag`](@ref).
