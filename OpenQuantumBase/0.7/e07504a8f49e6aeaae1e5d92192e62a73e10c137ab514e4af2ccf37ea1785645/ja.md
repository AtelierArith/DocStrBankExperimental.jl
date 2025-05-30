```
collective_operator(op, num_qubit; sp=false)
```

`num_qubit`量子ビットのシステムのための集合演算子を構築します。`op`は集合パウリ行列の名前です。例えば、以下のコードは$IZ + ZI$行列を構築します。`sp`がtrueに設定されている場合、スパース行列を生成します。

# 例

```julia-repl
julia> collective_operator("z", 2)
4×4 Array{Complex{Float64},2}:
 2.0+0.0im  0.0+0.0im  0.0+0.0im   0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im   0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im   0.0+0.0im
 0.0+0.0im  0.0+0.0im  0.0+0.0im  -2.0+0.0im
```
