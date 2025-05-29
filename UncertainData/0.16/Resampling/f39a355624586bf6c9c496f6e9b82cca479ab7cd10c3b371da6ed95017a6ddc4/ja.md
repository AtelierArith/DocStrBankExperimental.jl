```
resample(f::Function, x::AbstractUncertainValue, n::Int, args...; kwargs...)
```

`x`の供給分布に従って`n`要素のサンプルを抽出し、その後、長さ`n`の抽出に対して`f(x_draw, args...; kwargs...)`を呼び出します。
