```
restart_with!(semi, sol)
```

すべてのシステムの初期座標と速度を、解 `sol` の最終値に設定します。 [`semidiscretize`](@ref) を再度呼び出す必要があります。または、更新されたシステムを使用して別の [`Semidiscretization`](@ref) を作成できます。

# 引数

  * `semi`:   セミ離散化
  * `sol`:    `OrdinaryDiffEq` の `solve` によって返される `ODESolution`
