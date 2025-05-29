```
UserNSRunner
```

A `UserNSRunner` represents an "execution context", an object that bundles all necessary information to run commands within the container that contains our crossbuild environment.  Use `run()` to actually run commands within the `UserNSRunner`, and [`runshell()`](@ref) as a quick way to get an interactive shell within the crossbuild environment.
