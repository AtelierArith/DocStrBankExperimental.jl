### writepetsc(filename, mat :: Vector{Union{SparseMatrixCSC, Vector}}; int*type = nothing, scalar*type = nothing)

スパース行列またはベクトルを `filename` に書き込み、PETSc が理解できる形式にします。`PETSC_DIR` と `PETSC_ARCH` は、書き込まれる型のサイズを決定するために使用されます。`int_type` と `scalar_type` は、手動で希望する型を指定するために使用できます。
