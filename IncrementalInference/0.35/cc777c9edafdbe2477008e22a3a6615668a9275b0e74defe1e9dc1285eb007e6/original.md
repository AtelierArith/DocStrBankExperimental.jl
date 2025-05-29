```julia
repeatCSMStep!(hist, step; duplicate, enableLogging)

```

Repeat a solver state machine step – useful for debugging. 

Notes

  * use in combination with `solveTree!(fg, recordcliqs=[:0; :x7; ...])` – i.e. by clique frontals as identifier

      * to record everything, one can do: `recordcliqs=ls(fg)`.
  * `duplicate` avoids changing history or prime data in `hists`.
  * Replaces old API `sandboxCliqResolveStep`
  * Consider using this in combination with tools like [Revise.jl](https://github.com/timholy/Revise.jl)

      * On by default in VSCode.
  * Internally sets `csmc.enableLogging=false`

Example

```julia
using IncrementalInference

# generate a factor graph
fg = generateGraph_Kaess()

# solve and record everything
smtasks = Task[]
tree, _, = solveTree!(fg, smtasks=smtasks, recordcliqs=ls(fg));
# draw Bayes tree with graphviz and xdot installed
drawTree(tree, show=true)

# fetch histories
hists = fetchCliqHistoryAll!(smtasks);

# check a new csmc before step 2
csmc_ = repeatCSMStep!(hists, 1, 1)

# For use with VSCode debugging
@enter repeatCSMStep!(hists, 1, 1)

# or perhaps test a longer chain of changes
hists_ = deepcopy(hists)
repeatCSMStep!(hists_, 1, 4, duplicate=false)
repeatCSMStep!(hists_, 1, 5, duplicate=false)
repeatCSMStep!(hists_, 1, 6, duplicate=false)
```

DevNotes

  * TODO consolidate upstream with `FSM.sandboxStateMachineStep`

Related

[`solveTree!`](@ref), [`solveCliqUp!`](@ref), [`fetchCliqHistoryAll`](@ref), [`printCSMHistoryLogical`](@ref), [`printCSMHistorySequential`](@ref), cliqHistFilterTransitions
