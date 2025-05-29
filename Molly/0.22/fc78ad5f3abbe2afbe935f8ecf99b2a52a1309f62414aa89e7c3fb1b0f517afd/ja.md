```
SteepestDescentMinimizer(; <keyword arguments>)
```

最急降下エネルギー最小化。

# 引数

  * `step_size::D=0.01u"nm"`: 初期の最大変位。
  * `max_steps::Int=1000`: 最大ステップ数。
  * `tol::F=1000.0u"kJ * mol^-1 * nm^-1"`: 最小化を終了するための最大力。
  * `log_stream::L=devnull`: 最小化の進行状況を出力するストリーム。
