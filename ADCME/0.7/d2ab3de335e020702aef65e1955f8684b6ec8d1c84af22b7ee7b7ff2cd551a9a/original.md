```
pcl_linear_op(J::Array{Float64, 2}, W::Array{Float64,2})
```

For a linear operator 

$$
y = J^Tx + b
$$

The PCL backpropagation is given by  $H = JWJ^T$
