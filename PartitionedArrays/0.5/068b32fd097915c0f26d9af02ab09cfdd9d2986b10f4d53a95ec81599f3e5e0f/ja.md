```
with_mpi(f;comm=MPI.COMM_WORLD,duplicate_comm=true)
```

`f(a->distribute_with_mpi(a;comm,duplicate_comm))`を呼び出し、エラーがあった場合はMPIを中止します。これは、MPIを使用して関数`f`を実行する最も安全な方法です。

!!! note
    この関数は、MPIがまだ初期化されていない場合に`MPI.Init()`を呼び出します。

