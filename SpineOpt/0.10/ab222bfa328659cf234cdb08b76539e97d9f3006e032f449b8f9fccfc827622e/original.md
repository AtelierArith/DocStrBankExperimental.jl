```
build_model!(m; log_level)
```

Build given SpineOpt model:

  * create temporal and stochastic structures
  * add variables
  * add expressions
  * add constraints
  * set objective
  * initialize outputs

# Arguments

  * `log_level::Int`: an integer to control the log level.
