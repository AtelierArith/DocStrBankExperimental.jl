```
generate_random_greedy_color(g, reps)
```

This function generates a random greedy coloring of a graph. It uses the `random_greedy_color` function from the Graphs package.

# Arguments

  * `g`: The graph to be colored.
  * `reps`: The number of repetitions for the random greedy coloring algorithm.

# Examples

```julia
g = Graphs.grid_graph((5,5))
reps = 10
generate_random_greedy_color(g, reps)
```
