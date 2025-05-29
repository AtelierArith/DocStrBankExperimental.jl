```
hamming_weight_operator(num_qubit::Int64, op::String; sp=false)
```

サイズ `num_qubit` のシステムのためのハミング重み演算子を構築します。ハミング重み演算子のタイプは op によって指定されます: "x", "y" または "z"。`sp` が true に設定されている場合、スパース行列を生成します。

# 例

```julia-repl
julia> hamming_weight_operator(2,"z")
4×4 Array{Complex{Float64},2}:
 0.0+0.0im  0.0+0.0im  0.0+0.0im  0.0+0.0im
 0.0+0.0im  1.0+0.0im  0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im  1.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im  2.0+0.0im
```
