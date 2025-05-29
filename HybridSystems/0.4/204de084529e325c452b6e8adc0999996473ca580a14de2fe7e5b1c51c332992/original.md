```
GraphAutomaton(n::Int)
```

Creates a `GraphAutomaton` with `n` states 1, 2, ..., `n`. The automaton is initialized without any transitions, use [`add_transition!`](@ref) to add transitions.

## Examples

To create an automaton with 2 nodes 1, 2, self-loops of labels 1, a transition from 1 to 2 with label 2 and transition from 2 to 1 with label 3, do the following:

```jldoctest
julia> a = GraphAutomaton(2);

julia> add_transition!(a, 1, 1, 1) # Add a self-loop of label 1 for state 1
HybridSystems.GraphTransition{Graphs.SimpleGraphs.SimpleEdge{Int64}}(Edge 1 => 1, 1)

julia> add_transition!(a, 2, 2, 1) # Add a self-loop of label 1 for state 2
HybridSystems.GraphTransition{Graphs.SimpleGraphs.SimpleEdge{Int64}}(Edge 2 => 2, 2)

julia> add_transition!(a, 1, 2, 2) # Add a transition from state 1 to state 2 with label 2
HybridSystems.GraphTransition{Graphs.SimpleGraphs.SimpleEdge{Int64}}(Edge 1 => 2, 3)

julia> add_transition!(a, 2, 1, 3) # Add a transition from state 2 to state 1 with label 3
HybridSystems.GraphTransition{Graphs.SimpleGraphs.SimpleEdge{Int64}}(Edge 2 => 1, 4)
```
