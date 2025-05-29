```julia
μ0σ1(x::UniData; 
    corrected::Bool=false, 
    centered::Bool=false, 
    mean::Realo=nothing, 
    sd::Realo=nothing)
```

`x`を標準化した結果を返します（平均0、標準偏差1）。

`centered`がtrueの場合、オプション引数`corrected`、`centered`、`sd`を使って[`σ1`](@ref)を呼び出して`x`を等化します。

そうでない場合、`mean`として提供されていない場合は平均を計算し、標準偏差が提供されていない場合は`σ`[@ref]を呼び出してオプション引数`corrected`と`centered`を使って`x`を標準化します。

*例*

```julia
using PermutationTests
x=randn(3)
μx=μ(x) # 平均
σx=σ(x) # 標準偏差
xμ0=μ0(x) # 中心化データ

# 効率の降順
z1=μ0σ1(xμ0; sd=σx, centered=true)
z2=μ0σ1(xμ0; centered=true)
z3=μ0σ1(x; mean=μx, sd=σx)
z4=μ0σ1(x; mean=μx)
z5=μ0σ1(x; sd=σx)
z6=μ0σ1(x)

println(μ(z6)≈0. ? "OK" : "Error") # -> "Ok"
println(σ(z6)≈1. ? "OK" : "Error") # -> 'OK"
```
