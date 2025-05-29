```julia
σ1(x::UniData; 
    corrected::Bool=false, 
    centered::Bool=false, 
    mean::Realo=nothing, 
    sd::Realo=nothing)
```

`x`を等化します（単位標準偏差）。

`sd`が提供されている場合は、それに関して`x`を等化します。

そうでない場合は、オプション引数`corrected`、`centered`、および`mean`を使用して[`σ`](@ref)を呼び出し、`x`を等化します。

*例*

```julia
using PermutationTests
x=randn(3)
μx=μ(x) # 平均
σx=σ(x) # 標準偏差
xμ0=μ0(x) # 中心化データ

# 効率の降順
e1=σ1(xμ0; sd=σx, centered=true)
e2=σ1(xμ0; centered=true)
e3=σ1(x; mean=μx, sd=σx)
e4=σ1(x; mean=μx)

println(σ(e4)≈1.0 ? "OK" : "Error") # -> "OK"
```
