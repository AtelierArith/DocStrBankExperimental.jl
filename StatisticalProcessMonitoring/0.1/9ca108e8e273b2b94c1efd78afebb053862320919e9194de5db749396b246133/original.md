```
optimize_limit(CH::ControlChart, solver = :Bootstrap; hmax = 20.0, kw...)
```

Optimizes the control limit of a ControlChart object.

### Arguments

  * `CH::ControlChart`: The ControlChart object to optimize.
  * `solver::Symbol`: The solver algorithm to use (default: `:Bootstrap`).

### Keyword Arguments

  * `hmax::Float64`: The maximum value of the control limit. Only used for the bisection algorithm (default: 100.0)
  * `kw...`: Additional keyword arguments to pass to the algorithm.

### Returns

```
The optimized control limit value.
```

### Raises

```
ValueError: If the optimization method specified in settings is unknown.
```
