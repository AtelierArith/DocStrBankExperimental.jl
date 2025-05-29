```julia
function σ(x::UniData; 
    corrected::Bool=false, 
    centered::Bool=false, 
    mean::Realo=nothing) 
```

`x`の要素の母集団標準偏差またはその不偏標本推定量。

同じ引数で[`σ²`](@ref)を呼び出し、その平方根を返します。
