```
SetMaxEvals(p::DSProblem, max::Bool=true)
```

Set/unset parallel blackbox evaluations. The number of threads Julia was started with will be used.

Note that using parallel blackbox evaluations will only result in reduced runtime for problems that have long blackbox evaluations.
