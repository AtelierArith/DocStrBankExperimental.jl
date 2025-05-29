```
conf = GradientDescent(step_size_init, step_size_beta)
```

Configuration for stochastic gradient descent update with step size given by `(t::Int) -> step_size_init * (step_size_beta + 1) / (step_size_beta + t)` where `t` is the iteration number.
