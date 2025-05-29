```
struct GeneralDimensions{N,T1<:Tuple,T2<:Tuple} <: AbstractDimensions{N}
    to::T1
    from::T2
end
```

左側（`to`）と右側（`from`）のヒルベルト[`Space`](@ref)を記述する構造体です[`Operator`](@ref)。
