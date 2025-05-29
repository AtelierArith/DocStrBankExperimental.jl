```
LayoutIterator{T<:IterativeLayout,M<:AbstractMatrix}(algorithm, adj_matrix)
```

This type bundles an [`IterativeLayout`](@ref) with an adjacency matrix to form an iterable object whose items are the node positions.

## Example

```
for p in LayoutIterator(Stress(), adj_matrix)
    # do stuff with positions p
end
```
