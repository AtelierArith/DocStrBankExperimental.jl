```
wiring_diagram(agent; parentship_edges=true, wires=true)
wiring_diagram(agents; parentship_edges=true, wires=true)
wiring_diagram(groups; group_labels=nothing, parentship_edges=true, wires=true)
```

Render a Graphviz graph of agents in an hierarchy. By default, the graph shows edges between parent and child agents, and annotated wires.

Also see [`agent_hierarchy_mmd`](@ref).

# Examples

```julia
# Build a compound problem.
joint_system = ⊕(alice, bob, name = "joint system")

wiring_diagram(joint_system)

# Do not show edges between parents and children.
wiring_diagram(joint_system; parentship_edges=false)

# Only show listed agents.
wiring_diagram([alice, alice1, bob, bob1])

# Group agents into two clusters.
wiring_diagram([[alice, alice1], [bob, bob1]])
# Provide labels for clusters.
wiring_diagram([[alice, alice1], [bob, bob1]]; group_labels=["alice", "bob"], parentship_edges=false)
```
