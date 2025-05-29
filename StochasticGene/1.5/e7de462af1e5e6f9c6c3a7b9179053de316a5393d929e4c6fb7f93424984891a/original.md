```
num_all_parameters(transitions, R::Int, S, insertstep, reporter, coupling=tuple(), grid=nothing)
n = typeof(model.reporter) <: HMMReporterReporter ? model.reporter.n : 0
num_rates(transitions, R, S, insertstep) + n

`reporter` can either be a vector of noisepriors or of type HMMReporter
```

TBW
