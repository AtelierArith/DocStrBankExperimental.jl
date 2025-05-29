```
QuasiNewtonPreconditioner{E<:AbstractEvaluationType, F}
```

前処理を追加する

# フィールド

  * `preconditioner::F`: 前処理関数

# コンストラクタ

```
QuasiNewtonPreconditioner(
    preconditioner;
    evaluation::AbstractEvaluationType=AllocatingEvaluation()
)
```

勾配問題に前処理を追加する。

# 入力

  * `preconditioner`:   前処理関数、`(M, p, X) -> Y` のような割り当て関数または `(M, Y, p, X) -> Y` のような変更関数

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）または入力引数を変更してその結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、変更された引数は2番目の引数です。
