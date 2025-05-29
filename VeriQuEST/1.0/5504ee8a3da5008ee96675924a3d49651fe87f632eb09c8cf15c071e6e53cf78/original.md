```
get_vector_graph_colors(graph; reps=100)
```

Generates a vector of graph colors. It first generates a random greedy color for the graph (repeated `reps` times), then separates each color.

# Arguments

  * `graph`: The graph to be colored.
  * `reps`: The number of repetitions for generating the random greedy color (default is 100).

# Examples

```julia
get_vector_graph_colors(graph) # Returns a vector of graph colors
```
