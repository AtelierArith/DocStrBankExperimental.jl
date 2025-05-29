```
MadNLPSolver(nlp::AbstractNLPModel{T, VT}; options...) where {T, VT}
```

Instantiate a new `MadNLPSolver` associated to the nonlinear program `nlp::AbstractNLPModel`. The options are passed as optional arguments.

The constructor allocates all the memory required in the interior-point algorithm, so the main algorithm remains allocation free.
