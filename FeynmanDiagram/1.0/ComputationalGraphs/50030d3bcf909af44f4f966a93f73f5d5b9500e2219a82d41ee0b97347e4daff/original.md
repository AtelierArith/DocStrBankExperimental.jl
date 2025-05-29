```
function standardize_labels!(g::FeynmanGraph)

Finds all labels involved in `g` and its subgraphs and 
modifies `g` by relabeling in standardized order, e.g.,
(1, 4, 5, 7, ...) ↦ (1, 2, 3, 4, ....)
```

# Arguments:

  * `g::FeynmanGraph`: graph to be relabeled
