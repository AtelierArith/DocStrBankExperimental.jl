```
greedy_color(g; sort_degree=false, reps = 1)
```

Color graph `g` based on [Greedy Coloring Heuristics](https://en.wikipedia.org/wiki/Greedy_coloring)

The heuristics can be described as choosing a permutation of the vertices and assigning the lowest color index available iteratively in that order.

If `sort_degree` is true then the permutation is chosen in reverse sorted order of the degree of the vertices. `parallel` and `reps` are irrelevant in this case.

If `sort_degree` is false then `reps` colorings are obtained based on random permutations and the one using least colors is chosen.
