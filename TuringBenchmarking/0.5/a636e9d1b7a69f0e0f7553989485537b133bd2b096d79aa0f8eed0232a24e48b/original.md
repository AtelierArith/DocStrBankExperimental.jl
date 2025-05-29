```
make_turing_suite(model::Turing.Model; kwargs...)
```

Create default benchmark suite for `model`.

# Keyword arguments

  * `adbackends`: a collection of adbackends to use, specified either as a type from

ADTypes.jl or using a `Symbol`. Defaults to `ADTypes.AbstractADType[ADTypes.AutoForwardDiff(chunksize=0), ADTypes.AutoReverseDiff(), ADTypes.AutoReverseDiff(compile=true), ADTypes.AutoZygote()]`.

  * `run_once=true`: if `true`, the body of each benchmark will be run once to avoid compilation to be included in the timings (this may occur if compilation runs longer than the allowed time limit).
  * `check=false`: if `true`, the log-density evaluations and the gradients will be compared against each other to ensure that they are consistent. Note that this will force `run_once=true`.
  * `error_on_failed_check=false`: if `true`, an error will be thrown if the check fails rather than just printing a warning, as is done by default.
  * `error_on_failed_backend=false`: if `true`, an error will be thrown if the evaluation of the log-density or the gradient fails for any of the backends rather than just printing a warning, as is done by default.
  * `varinfo`: the `VarInfo` to use. Defaults to `DynamicPPL.VarInfo(model)`.
  * `sampler`: the `Sampler` to use. Defaults to `nothing` (i.e. no sampler).
  * `context`: the `Context` to use. Defaults to `DynamicPPL.DefaultContext()`.
  * `θ`: the parameters to use. Defaults to `rand(Vector, model)`.
  * `θ_linked`: the linked parameters to use. Defaults to `randn(d)` where `d`  is the length of the linked parameters..
  * `atol`: the absolute tolerance to use for comparisons.
  * `rtol`: the relative tolerance to use for comparisons.

# Notes

  * A separate "parameter" instance (`DynamicPPL.VarInfo`) will be created for *each test*. Hence if you have a particularly large model, you might want to only pass one `adbackend` at the time.
