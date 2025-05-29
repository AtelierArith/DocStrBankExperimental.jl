```
pcl_linear_op(J::Array{Float64, 2}, W::Array{Float64,2})
```

線形演算子について 

$$
y = J^Tx + b
$$

PCLの逆伝播は $H = JWJ^T$ で与えられます。
