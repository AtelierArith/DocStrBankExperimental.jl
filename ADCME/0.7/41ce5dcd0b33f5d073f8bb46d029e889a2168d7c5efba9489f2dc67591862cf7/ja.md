```
pcl_sparse_solve(indices::Array{Int64, 2}, 
    vals::Array{Float64, 1}, 
    u::Array{Float64, 1}, 
    hessian_u::Array{Float64, 2}, grad_u::Array{Float64, 1})
```

ヘッセ行列の逆伝播 

$$
Au = f
$$

`A` はスパース行列によって与えられます（非ゼロエントリはベクトル $a$ です）。この関数は、$u$ に関するヘッセ行列を $A$ に関するヘッセ行列に逆伝播します。
