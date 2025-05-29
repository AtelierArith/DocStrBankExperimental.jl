```
PETScSNES(; petsclib = missing, autodiff = nothing, mpi_comm = missing, kwargs...)
```

[PETSc.jl](https://github.com/JuliaParallel/PETSc.jl) SNESソルバーのラッパーです。

### キーワード引数

  * `petsclib`: 使用するPETScライブラリ。`missing`に設定されている場合、問題の要素タイプに基づいて`PETSc.petsclibs`内の最初の利用可能なPETScライブラリを使用します。
  * `autodiff`: ヤコビアンを生成するためのメソッドの選択。デフォルトは`nothing`で、これは問題の仕様に従ってデフォルトが選択されることを意味します。これは、NonlinearSolve.jlでサポートされているバックエンドに依存する有効なADTypes.jl自動微分タイプであることができます。`missing`に設定されている場合、PETScは有限差分を使用してヤコビアンを計算します。
  * `mpi_comm`: 使用するMPIコミュニケーター。`missing`に設定されている場合、`MPI.COMM_SELF`を使用します。
  * `kwargs`: PETSc SNESソルバーに渡されるキーワード引数。詳細については、[PETSc SNESドキュメント](https://petsc.org/release/manual/snes/)および[SNESSetFromOptions](https://petsc.org/release/manualpages/SNES/SNESSetFromOptions)を参照してください。

### `CommonSolve.solve`を介したオプション

これらのオプションは、`solve`からPETSc SNESソルバーに転送されます。これらが`kwargs`に提供されている場合、無視されます。

| `solve`オプション | PETSc SNESオプション |
|:------------ |:--------------- |
| `atol`       | `snes_atol`     |
| `rtol`       | `snes_rtol`     |
| `maxiters`   | `snes_max_it`   |
| `show_trace` | `snes_monitor`  |

!!! note
    このアルゴリズムは、`PETSc.jl`がインストールされていて読み込まれている場合にのみ利用可能です。

