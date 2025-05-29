```
Diagnostic(calc, prob; freq=1, nsteps=100, ndata=ceil(Int, (nsteps+1)/freq))
```

Construct a diagnostic that stores the result of `calc(prob)` with frequency `freq`.

# Keywords

  * `freq`: Diagnostic is saved every `freq` steps.
  * `nsteps`: The total number of steps in problem.
  * `ndata`: The number of diagnostics to be saved.
