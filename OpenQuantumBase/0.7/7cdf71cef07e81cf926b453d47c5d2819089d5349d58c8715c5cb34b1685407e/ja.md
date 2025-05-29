```
gibbs_state(h, β)
```

行列 `h` のギブス状態を温度 `T` (mK) で計算します。

# 例

```julia-repl
julia> gibbs_state(σz, 10)
2×2 Array{Complex{Float64},2}:
 0.178338+0.0im       0.0+0.0im
      0.0+0.0im  0.821662+0.0im
```
