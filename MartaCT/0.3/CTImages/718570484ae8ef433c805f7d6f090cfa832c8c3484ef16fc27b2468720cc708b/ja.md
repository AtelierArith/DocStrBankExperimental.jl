```
rescale(x::AbstractArray, slope::Number, intercept::Number; window)
```

`x`を`slope`と`intercept`を用いて線形スケーリングします：`x * slope + intercept`。

関連情報: [`rescale!`](@ref)
