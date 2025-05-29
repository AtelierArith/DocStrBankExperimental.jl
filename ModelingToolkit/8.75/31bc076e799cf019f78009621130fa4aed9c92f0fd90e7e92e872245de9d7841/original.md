```julia
struct OptimizationSystem <: ModelingToolkit.AbstractOptimizationSystem
```

A scalar equation for optimization.

# Fields

  * `tag`: A tag for the system. If two systems have the same tag, then they are structurally identical.

  * `op`: Objective function of the system.
  * `states`: Unknown variables.
  * `ps`: Parameters.
  * `var_to_name`: Array variables.
  * `observed`: Observed variables.
  * `constraints`: List of constraint equations of the system.
  * `name`: The name of the system.
  * `systems`: The internal systems. These are required to have unique names.
  * `defaults`: The default values to use when initial guess and/or parameters are not supplied in `OptimizationProblem`.

  * `metadata`: Metadata for the system, to be used by downstream packages.

  * `gui_metadata`: Metadata for MTK GUI.

  * `complete`: If a model `sys` is complete, then `sys.x` no longer performs namespacing.

  * `parent`: The hierarchical parent system before simplification.

# Examples

```julia
@variables x y z
@parameters a b c

obj = a * (y - x) + x * (b - z) - y + x * y - c * z
cons = [x^2 + y^2 ≲ 1]
@named os = OptimizationSystem(obj, [x, y, z], [a, b, c]; constraints = cons)
```
