```
find_partitions(model, p_fun, options, args...; show_timer=false, kwargs...)
```

Performs parameter space partitioning.

# Arguments

  * `model`: a model function that returns predictions given a vector of parameters
  * `p_fun`: a function that that evaluates the qualitative data pattern
  * `options`: a set of options for configuring the algorithm
  * `args...`: arguments passed to `model` and `p_fun`

# Keywords

  * `show_timer=false`: displays timer and progress bar if true
  * `kwargs...`: keyword arguments passed to `model` and `p_fun`
