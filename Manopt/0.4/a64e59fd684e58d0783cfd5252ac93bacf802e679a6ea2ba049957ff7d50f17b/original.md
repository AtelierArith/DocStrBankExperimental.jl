```
decorate_state!(s::AbstractManoptSolverState)
```

decorate the [`AbstractManoptSolverState`](@ref)`s` with specific decorators.

# Optional arguments

optional arguments provide necessary details on the decorators.

  * `debug`:         (`Array{Union{Symbol,DebugAction,String,Int},1}()`) a set of symbols representing [`DebugAction`](@ref)s, `Strings` used as dividers and a sub-sampling integer. These are passed as a [`DebugGroup`](@ref) within `:Iteration` to the [`DebugSolverState`](@ref) decorator dictionary. Only exception is `:Stop` that is passed to `:Stop`.
  * `record`:        (`Array{Union{Symbol,RecordAction,Int},1}()`) specify recordings by using `Symbol`s or [`RecordAction`](@ref)s directly. An integer can again be used for only recording every $i$th iteration.
  * `return_state`:  (`false`) indicate whether to wrap the options in a [`ReturnSolverState`](@ref), indicating that the solver should return options and not (only) the minimizer.

other keywords are ignored.

# See also

[`DebugSolverState`](@ref), [`RecordSolverState`](@ref), [`ReturnSolverState`](@ref)
