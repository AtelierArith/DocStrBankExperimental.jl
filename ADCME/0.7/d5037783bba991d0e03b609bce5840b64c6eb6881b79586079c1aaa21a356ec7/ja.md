```
adjoint(A::mpi_SparseTensor)
```

`A`の随伴行列、すなわち`A'`を返します。各MPIランクは同じ数の行を所有します。
