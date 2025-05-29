```
krylov_solve(method, args...; kwargs...)
krylov_solve(Val(method), args...; kwargs...)
```

指定された `method` によって適切なアウトオブプレース（ブロック）Krylov メソッドにディスパッチする汎用関数です。両方の呼び出しで、`method` はシンボル（例えば `:cg`、`:gmres` または `:block_minres`）です。

便利さのためにプレーンなシンボル `method` を渡すか、`Val(method)` でラップして完全なコンパイル時の特殊化を有効にし、型推論を改善し、最大のパフォーマンスを達成します。
