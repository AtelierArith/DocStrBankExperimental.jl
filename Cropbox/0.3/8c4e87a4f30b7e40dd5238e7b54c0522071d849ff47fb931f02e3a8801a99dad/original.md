```
evaluate(obs, est; <keyword arguments>) -> Number | Tuple
```

Compare observation data `obs` and estimation data `est` with a choice of evaluation metric.

# Arguments

  * `obs::DataFrame`: observation data to be used for evaluation.
  * `est::DataFrame`: estimated data from simulation.

# Keyword Arguments

## Layout

  * `index`: variables referring to index columns of the output.
  * `target`: variables referring to non-index columns of the output.

## Evaluation

  * `metric=nothing`: evaluation metric (`:rmse`, `:nrmse`, `:mae`, `:mape`, `:ef`, `:dr`); default is RMSE.

See also: [`evaluate`](@ref)

# Examples

```julia-repl
julia> obs = DataFrame(time = [1, 2, 3]u"hr", b = [10, 20, 30]u"g");

julia> est = DataFrame(time = [1, 2, 3]u"hr", b = [10, 20, 30]u"g", c = [11, 19, 31]u"g");

julia> evaluate(obs, est; index = :time, target = :b)
0.0 g

julia> evaluate(obs, est; index = :time, target = :b => :c)
1.0 g
```
