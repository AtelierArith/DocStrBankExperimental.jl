```
num_all_parameters(transitions, R::Int, S, insertstep, reporter, coupling=tuple(), grid=nothing)
n = typeof(model.reporter) <: HMMReporterReporter ? model.reporter.n : 0
num_rates(transitions, R, S, insertstep) + n

`reporter` はノイズプライヤーのベクトルまたは HMMReporter 型である可能性があります
```
