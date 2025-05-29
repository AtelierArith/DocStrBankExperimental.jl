```
mpi_SparseTensor(sp::Union{SparseTensor, SparseMatrixCSC{Float64,Int64}}, 
    ilower::Union{Int64, Missing} = missing,
    iupper::Union{Int64, Missing} = missing)
```

`SparseTensor`またはスパース配列から`mpi_SparseTensor`を構築します。
