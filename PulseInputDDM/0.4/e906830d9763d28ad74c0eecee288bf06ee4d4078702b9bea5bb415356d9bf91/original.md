Optimize model parameters for a `neuralDDM`.

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

Arguments: 

  * `model`: an instance of a `neuralDDM`.
  * `data`: an instance of a `neuralDDM`.

Returns:

  * `model`: an instance of a `neuralDDM`.
