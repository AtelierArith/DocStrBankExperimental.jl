```
mutable struct DirectTrajOptProblem <: AbstractProblem
```

DirectTrajOptProblemを設定し、解決するために必要なすべての情報と、ソルバーが終了した後の解を格納します。

# フィールド

  * `optimizer::Ipopt.Optimizer`: Ipoptオプティマイザーオブジェクト
