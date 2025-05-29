```
workspace = krylov_workspace(method, args...; kwargs...)
workspace = krylov_workspace(Val(method), args...; kwargs...)
```

[`KrylovWorkspace`](@ref)および[`BlockKrylovWorkspace`](@ref)の各サブタイプに対して適切なワークスペースコンストラクタにディスパッチする汎用関数です。両方の呼び出しで、`method`はシンボル（例えば`:cg`、`:gmres`、または`:block_minres`）であり、ワークスペースが必要な（ブロック）クリロフ法を指定します。返されたワークスペースは、後で[`krylov_solve!`](@ref)によって（ブロック）クリロフ法をインプレースで実行するために使用できます。

便利さのためにプレーンシンボル`method`を渡すか、`Val(method)`でラップして完全なコンパイル時の特殊化を有効にし、型推論を改善し、最大のパフォーマンスを達成します。
