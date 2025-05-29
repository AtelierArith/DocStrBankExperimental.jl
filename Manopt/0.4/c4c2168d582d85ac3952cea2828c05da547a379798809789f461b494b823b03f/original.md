```
DebugEntry <: DebugAction
```

print a certain fields entry during the iterates, where a `format` can be specified how to print the entry.

# Additional fields

  * `field`: symbol the entry can be accessed with within [`AbstractManoptSolverState`](@ref)

# Constructor

```
DebugEntry(f; prefix="$f:", format = "$prefix %s", io=stdout)
```
