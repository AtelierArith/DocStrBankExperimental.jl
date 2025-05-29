```
ScipyOptimizerMinimize(sess::PyObject, opt::PyObject; kwargs...)
```

スカラーTensorを最小化します。最適化の対象となる変数は、最適化の終了時にインプレースで更新されます。

このメソッドは、`minimize`とは異なり、最小化Opを返すだけではなく、実際にコマンドを実行してセッションを制御することによって最小化を行います https://www.tensorflow.org/api_docs/python/tf/contrib/opt/ScipyOptimizerInterface。さらに、[`ScipyOptimizerInterface`](@ref)および[`BFGS!`](@ref)も参照してください。

  * feed_dict: session.runへの呼び出しに渡されるフィード辞書。
  * fetches: loss_callbackに位置引数として供給されるTensorのリスト。
  * step_callback: 各最適化ステップで呼び出される関数; 引数は、すべての最適化変数の現在の値を単一のベクトルにパックしたものです。
  * loss_callback: 損失と勾配が計算されるたびに呼び出される関数で、評価されたfetchesが位置引数として供給されます。
  * run_kwargs: session.runに渡すkwargs。
