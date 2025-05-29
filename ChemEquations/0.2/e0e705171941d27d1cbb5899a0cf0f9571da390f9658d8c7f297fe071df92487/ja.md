```julia
balancematrix(
    equation::ChemEquations.ChemEquation{T<:(Union{Complex{S}, S} where S<:Integer)};
    fractions
) -> Any

```

[`balancematrix(::ChemEquation)`](@ref)と同様ですが、整数係数の化学反応式用です。

デフォルトでは、整数行列の解は整数として表示されます。`fractions`がtrueの場合、代わりに有理数の分数として表示されます。
