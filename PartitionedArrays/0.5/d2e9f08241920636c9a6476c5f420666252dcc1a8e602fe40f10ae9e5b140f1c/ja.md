```
distribute_with_mpi(a;comm::MPI.Comm=MPI.COMM_WORLD,duplicate_comm=true)
```

コレクション `a` のアイテムを指定された MPI 通信者 `comm` のランクに分配することで [`MPIArray`](@ref) インスタンスを作成します。各ランクは正確に1つのアイテムを受け取るため、`length(a)` と通信者のサイズは一致する必要があります。各ランクに複数のアイテムを格納できる配列については、[`PVector`](@ref) または [`PSparseMatrix`](@ref) を参照してください。`duplicate_comm=false` の場合、結果は指定された通信者の所有権を引き継ぎます。そうでない場合は、`MPI.Comm_dup(comm)` でコピーが行われます。

!!! note
    この関数は、MPI がまだ初期化されていない場合に `MPI.Init()` を呼び出します。

