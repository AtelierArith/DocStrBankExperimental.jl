```julia
struct EnsembleProblem{T, T2, T3, T4, T5} <: SciMLBase.AbstractEnsembleProblem
```

直接問題のベクトルが渡される古い使用法のためのコンストラクタです。

!!! warning
    このコンストラクタは廃止予定です。代わりに `prob_func` を使用した標準のアンサンブル構文を使用してください。

