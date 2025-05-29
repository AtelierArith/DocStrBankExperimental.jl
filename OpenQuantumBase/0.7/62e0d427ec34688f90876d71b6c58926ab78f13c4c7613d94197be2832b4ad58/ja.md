```
low_level_matrix(M, lvl)
```

エネルギー `lvl` レベルを含む低エネルギーサブスペースに投影された行列 `M` を計算します。

# 例

```julia-repl
julia> low_level_matrix(σx⊗σx, 2)
4×4 Array{Complex{Float64},2}:
 -0.5+0.0im   0.0+0.0im   0.0+0.0im   0.5+0.0im
  0.0+0.0im  -0.5+0.0im   0.5+0.0im   0.0+0.0im
  0.0+0.0im   0.5+0.0im  -0.5+0.0im   0.0+0.0im
  0.5+0.0im   0.0+0.0im   0.0+0.0im  -0.5+0.0im
```
