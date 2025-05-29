```
function relabel!(g::FeynmanGraph, map::Dict{Int,Int})

Relabels the quantum operators in `g` and its subgraphs according to `map`.
For example, `map = {1=>2, 3=>2}`` will find all quantum operators with labels 1 and 3, and then map them to 2.
```

# Arguments:

  * `g::FeynmanGraph`: graph to be modified
  * `map`: mapping from old labels to the new ones
