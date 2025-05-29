```
resample(f::Function, 
    x::AbstractUncertainValue, y::AbstractUncertainValue,
    n::Int, args...; kwargs...)
```

`x`の供給分布に従って`n`要素のサンプルを引き出し、`y`の供給分布に従って`n`要素のサンプルを引き出します。次に、長さ`n`のサンプルに対して`f(x_draw, y_draw, args...; kwargs...)`を呼び出します。
