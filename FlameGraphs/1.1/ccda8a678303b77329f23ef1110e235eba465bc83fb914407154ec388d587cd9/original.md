```
g = flamegraph(data=Profile.fetch(); lidict=nothing, C=false, combine=true, recur=:off, norepl=true, pruned=[], filter=nothing)
```

Compute a graph representing profiling data. To compute it for the currently-collected profiling information, omit both `data` and `lidict`; if you are computing it for saved profiling data, supply both. (`data` and `lidict` must be a matched pair from `Profile.retrieve()`.)

You can control the strategy with the following keywords:

  * `C`: if `true`, include stackframes collected from `ccall`ed code.
  * `recur` (supported on Julia 1.4+): represent recursive calls as if they corresponded to iteration.
  * `norepl`: if true, the portions of stacktraces deeper than `REPL.eval_user_input` are discarded.
  * `pruned`: a list of `(funcname, filename)` pairs that trigger the termination of this branch of the flame graph. You can use this to prevent very "tall" graphs from deeply-recursive calls, e.g., `pruned = [("sort!", "sort.jl")]` would omit nodes corresponding to Julia's `sort!` function and anything called by it. See also `recur` for an alternative strategy.
  * `combine`: if true, instruction pointers that correspond to the same line of code are combined into a single stackframe
  * `filter`: drop all branches that do not satisfy the filter condition. `Condition` can be `string`, `regex` or any function, that can be applied to `NodeData`. For example, `filter = "mapslices"` or equivalently `filter = x -> (x.sf.func == :mapslices)` removes all branches that do not contain `mapslices` Node as a child or ancestor.
  * `threads::Union{Int,AbstractVector{Int},Nothing}`: specify which threads to include samples from. `nothing` returns all.
  * `tasks::Union{Int,AbstractVector{Int},Nothing}`: specify which tasks to include samples from. `nothing` returns all.

!!! compat 1.8     The `threads` and `tasks` kwargs require julia 1.8

`g` can be inspected using [`AbstractTrees.jl`'s](https://github.com/JuliaCollections/AbstractTrees.jl) `print_tree`.
