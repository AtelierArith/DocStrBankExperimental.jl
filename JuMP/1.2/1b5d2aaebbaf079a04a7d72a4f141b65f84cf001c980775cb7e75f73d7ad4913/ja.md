```
optimize!(
    model::Model;
    ignore_optimize_hook = (model.optimize_hook === nothing),
    _differentiation_backend::MOI.Nonlinear.AbstractAutomaticDifferentiation =
        MOI.Nonlinear.SparseReverseMode(),
    kwargs...,
)
```

モデルを最適化します。

まだオプティマイザーが設定されていない場合（[`set_optimizer`](@ref)を参照）、[`NoOptimizer`](@ref)エラーがスローされます。

`ignore_optimize_hook == true`の場合、最適化フックは無視され、フックが設定されていないかのようにモデルが解決されます。キーワード引数`kwargs`は`optimize_hook`に渡されます。`optimize_hook`が`nothing`であり、キーワード引数が提供された場合、エラーがスローされます。

## 実験的機能

これらの機能は、今後のJuMPのバージョンで変更または削除される可能性があります。

`_differentiation_backend`を渡して、非線形プログラムの導関数を計算するために使用される[`MOI.Nonlinear.AbstractAutomaticDifferentiation`](@ref)バックエンドを設定します。

`:ExprGraph`のみが必要な場合、`_differentiation_backend = MOI.Nonlinear.ExprGraphOnly()`を渡す方が効率的です。
