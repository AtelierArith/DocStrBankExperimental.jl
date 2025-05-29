```
setup_parameter_optimization(model, state0, param, dt, forces, G, opt_cfg = optimization_config(model, param);
                                                        grad_type = :adjoint,
                                                        config = nothing,
                                                        print = 1,
                                                        copy_case = true,
                                                        param_obj = false,
                                                        kwarg...)
```

`simulate`への入力によって定義されたケースを最適化するための関数ハンドルを設定します。目的関数 `G` は、すべてのステップにわたる合計の形であるべきであり、合計の各要素は `model, state, dt, step_no, forces` によって評価されます。

一般的に、いずれかの関数を呼び出すと、データのDictが変更されます。オプションは次のとおりです： F*o(x) -> 目的を評価 dF*o(dFdx, x) -> 目的の勾配を評価し、dFdxを変更します（F*oの評価をトリガーする可能性があります） F*and_dF(F, dFdx, x) -> Fおよび/またはdFを評価します。nothingの値は、対応するエントリがスキップされることを意味します。
