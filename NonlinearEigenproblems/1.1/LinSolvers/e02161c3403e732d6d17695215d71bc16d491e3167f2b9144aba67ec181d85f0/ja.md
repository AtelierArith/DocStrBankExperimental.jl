```
GMRESLinSolverCreator(;kwargs...)
```

これはGMRES法のためのクリエーターです。線形システムソルバーとしてGMRESを使用したい場合は、このオブジェクトをインスタンス化してください。`kwargs`は保存され、gmresへの呼び出しでキーワード引数として使用されます。キーワードのリストは[IterativeSolvers.jlマニュアル](https://juliamath.github.io/IterativeSolvers.jl/dev/linear_systems/gmres/)を参照してください。
