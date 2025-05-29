```
pcl_sparse_solve(indices::Array{Int64, 2}, 
    vals::Array{Float64, 1}, 
    u::Array{Float64, 1}, 
    hessian_u::Array{Float64, 2}, grad_u::Array{Float64, 1})
```

Hessian backpropagation for 

$$
Au = f
$$

`A` is given by a sparse matrix (the nonzero entries are a vector $a$). This function  back-propagates the Hessian w.r.t. $u$ to the Hessian w.r.t. $A$. 
