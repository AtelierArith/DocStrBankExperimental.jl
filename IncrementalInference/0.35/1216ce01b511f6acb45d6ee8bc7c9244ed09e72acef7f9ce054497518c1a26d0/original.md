```julia
solveCliqUp!(fg, tree, cliqid; ...)
solveCliqUp!(fg, tree, cliqid, solveKey; ...)
solveCliqUp!(
    fg,
    tree,
    cliqid,
    solveKey,
    beliefMessages;
    verbose,
    recordcliq
)

```

Perform inference in the upward direction over one clique in the Bayes tree according to `opt::SolverParams`.

Example

```julia
tree = buildTreeReset!(fg)
hist, upMessageOut = solveCliqUp!(fg, tree, 2)
```

Notes

  * Modifies fg with new values
  * Calculates up messages from fg if not provided

DevNotes

  * Test isfixedlag
  * Test recordcliq

Related [`solveTree!`](@ref), [`buildTreeReset!`](@ref), [`printCliqHistorySummary`](@ref), [`repeatCSMStep!`](@ref), `sandboxStateMachineStep`
