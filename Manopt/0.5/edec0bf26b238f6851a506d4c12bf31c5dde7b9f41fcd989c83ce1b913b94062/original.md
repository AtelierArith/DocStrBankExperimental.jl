```
DebugCost <: DebugAction
```

print the current cost function value, see [`get_cost`](@ref).

# Constructors

```
DebugCost()
```

# Parameters

  * `format="$prefix %f"`: format to print the output
  * `io=stdout`: default stream to print the debug to.
  * `long=false`: short form to set the format to `f(x):` (default) or `current cost:` and the cost
