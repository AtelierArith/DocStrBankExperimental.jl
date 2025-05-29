```julia
histGraphStateMachineTransitions(
    stateVisits,
    allStates;
    maxpenwidth,
    minpenwidth
)

```

Create a `Graphs.incdict` object and populate with nodes (states) and edges (transitions) according to the contents of parameters passed in.

Notes:

  * Current implementation repeats duplicate transitions as new edges.
