```julia
solveTree!(dfgl; ...)
solveTree!(
    dfgl,
    oldtree;
    timeout,
    storeOld,
    verbose,
    verbosefid,
    delaycliqs,
    recordcliqs,
    limititercliqs,
    injectDelayBefore,
    skipcliqids,
    eliminationOrder,
    eliminationConstraints,
    smtasks,
    dotreedraw,
    runtaskmonitor,
    algorithm,
    solveKey,
    multithread
)

```

Perform inference over the Bayes tree according to `opt::SolverParams` and keyword arguments.

Notes

  * Aliased with `solveGraph!`
  * Variety of options, including fixed-lag solving – see `getSolverParams(fg)` for details.

      * See online Documentation for more details: https://juliarobotics.org/Caesar.jl/latest/
  * Latest result always stored in `solvekey=:default`.
  * Experimental `storeOld::Bool=true` will duplicate the current result as supersolve `:default_k`.

      * Based on `solvable==1` assumption.
  * `limititercliqs` allows user to limit the number of iterations a specific CSM does.
  * keywords `verbose` and `verbosefid::IOStream` can be used together to to send output to file or default `stdout`.
  * keyword `recordcliqs=[:x0; :x7...]` identifies by frontals which cliques to record CSM steps.

      * See [`repeatCSMStep!`](@ref), [`printCSMHistoryLogical`](@ref), [`printCSMHistorySequential`](@ref)

DevNotes

  * TODO Change keyword arguments to new @parameter `SolverOptions` type.

Example

```julia
# pass in old `tree` to enable compute recycling -- see online Documentation for more details
tree = solveTree!(fg [,tree])
```

Related

`solveGraph!`, [`solveCliqUp!`](@ref), [`solveCliqDown!`](@ref), [`buildTreeReset!`](@ref), [`repeatCSMStep`](@ref), [`printCSMHistoryLogical`](@ref)
