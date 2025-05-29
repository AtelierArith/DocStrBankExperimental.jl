`neuralDDM`のモデルパラメータを最適化します。

```julia
fit(
    model,
    data;
    x_tol,
    f_tol,
    g_tol,
    iterations,
    show_trace,
    outer_iterations,
    scaled,
    extended_trace
)

```

引数:

  * `model`: `neuralDDM`のインスタンス。
  * `data`: `neuralDDM`のインスタンス。

返り値:

  * `model`: `neuralDDM`のインスタンス。
