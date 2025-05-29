```
has_interaction{(N::AbstractEcologicalNetwork, i::NT, j::NT)
```

This function returns `true` if the interaction between `i` and `j` is not 0. This refers to species by their names/values, and is the recommended way to test for the presence of an interaction.

Use `N[i,j]` if you need to get the value of the interaction.
