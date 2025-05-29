```
remake(prob::AbstractSciMLProblem; u0 = missing, p = missing, interpret_symbolicmap = true, use_defaults = false)
```

Remake the given problem `prob`. If `u0` or `p` are given, they will be used instead of the unknowns/parameters of the problem. Either of them can be a symbolic map if the problem has an associated system. If `interpret_symbolicmap == false`, `p` will never be interpreted as a symbolic map and used as-is for parameters. `use_defaults` allows controlling whether the default values from the system will be used to calculate missing values in the symbolic map passed to `u0` or `p`. It is only valid when either `u0` or `p` have been explicitly provided as a symbolic map and the problem has an associated system.
