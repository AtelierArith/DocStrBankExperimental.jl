```
optimize_limit(CH::ControlChart, solver::Symbol = :Bootstrap; kw...)
```

Optimizes the control limit of a ControlChart object, without modifying the original ControlChart object.

### Arguments

  * `CH::ControlChart`: The ControlChart object to optimize.
  * `solver::Symbol`: The solver algorithm to use (default: `:Bootstrap`).

### Keyword Arguments

  * `hmax::Float64`: The maximum value of the control limit. Used only for the bisection algorithm (default: 100.0)
  * `kw...`: Additional keyword arguments to pass to the algorithm.

### Returns

```
The optimized control limit value.
```

### Raises

```
ValueError: If the optimization method specified in settings is unknown.
```

### Example

```
optimize_limit(my_chart, settings=OptSettings(ic_solver=:SA))
```
