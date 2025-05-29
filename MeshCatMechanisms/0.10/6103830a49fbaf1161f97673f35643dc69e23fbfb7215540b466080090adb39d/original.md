```
set_configuration!(mvis::MechanismVisualizer, args...)
```

Set the configuration of the mechanism visualizer and re-render it.

# Examples

```julia-repl
julia> set_configuration!(vis, [1., 2., 3.])
```

```julia-repl
julia> set_configuration!(vis, findjoint(robot, "shoulder"), 1.0)
```
