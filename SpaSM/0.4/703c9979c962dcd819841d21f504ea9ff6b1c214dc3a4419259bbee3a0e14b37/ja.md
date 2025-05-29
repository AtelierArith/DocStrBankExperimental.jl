```
sparse_triangular_solve(LU::LU{F}, B::CSR{F})
sparse_triangular_solve(U::CSR{F}, B::CSR{F}, qinv::Vector{Int32})
```

`X`*`LU.U` == `B`、または `X`*`U` = `B` をスパース行列で解きます。`U` のピボット位置は `qinv` で示されます。

解 `X` をスパース行列として返すか、解がない場合は `nothing` を返します。
