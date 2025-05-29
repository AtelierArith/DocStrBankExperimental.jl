```
activate_multithread(backend::CPU; nthreads=1) = BLAS.set_num_threads(nthreads)
```

BLASスレッドの数を設定するための便利な関数です。

# 入力引数

  * `backend` は唯一の必須入力で、`KernelAbstractions.jl`からの `CPU()` でなければなりません。
  * `nthreads` はBLASコアの数を設定するために使用できます（デフォルトは `nthreads=1` です）。
