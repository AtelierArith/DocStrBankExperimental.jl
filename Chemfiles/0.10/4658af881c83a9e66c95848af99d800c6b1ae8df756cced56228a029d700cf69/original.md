```julia
Trajectory(f::Function, args...) -> Any

```

Apply the function `f` to the result of `Trajectory(args...)` and close the resulting trajectory upon completion, similar to `open(f, args...)`.
