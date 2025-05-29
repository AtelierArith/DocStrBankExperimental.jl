```julia
leaf(trajectory, phasepoint, is_initial)

```

Information for a tree made of a single node. When `is_initial == true`, this is the first node. The first value is either

1. `nothing` for a divergent node,
2. a tuple containing the proposal `ζ`, the log weight (probability) of the node `ω`, the

turn statistics `τ` (never tested with `is_turning` for leaf nodes). The second value is the visited node information.

# Examples

```julia

```
