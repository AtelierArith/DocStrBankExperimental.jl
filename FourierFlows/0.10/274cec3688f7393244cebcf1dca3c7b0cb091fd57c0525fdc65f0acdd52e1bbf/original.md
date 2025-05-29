```
stepforward!(prob::Problem, diags, nsteps::Int)
```

Step forward `prob` for `nsteps`, incrementing `diags` along the way. `diags` may be a  single `Diagnostic` or a `Vector` of `Diagnostic`s.
