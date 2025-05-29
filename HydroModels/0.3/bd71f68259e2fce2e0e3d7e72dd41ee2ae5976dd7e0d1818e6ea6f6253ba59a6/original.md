```
@unithydro name begin ... end
```

Macro to simplify the construction of a `UnitHydrograph` object.

# Usage

```julia
@unithydro :my_uh begin
    uh_func = begin
        # Define piecewise UH function: max_time => expression
        lag => 0.5 * (t / lag)^2.5
        2lag => 1.0 - 0.5 * abs(2 - t / lag)^2.5
    end
    uh_vars = [runoff] # Input variable(s)
    configs = (solvetype=:SPARSE, suffix=:_routed)
end
```

Defines a `UnitHydrograph` with the specified name, piecewise UH function definition (`uh_func`), input variables (`uh_vars`), and configuration (`configs`) within the `begin...end` block.

# Arguments

  * `name`: (Optional) Symbol for the unit hydrograph name.
  * `block`: A `begin...end` block containing assignments for `uh_func`, `uh_vars`, and optionally `configs`.

# Returns

  * A `UnitHydrograph` instance.
