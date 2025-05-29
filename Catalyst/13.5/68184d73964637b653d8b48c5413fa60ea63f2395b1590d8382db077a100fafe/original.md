```
Graph(rn::ReactionSystem)
```

Converts a [`ReactionSystem`](@ref) into a Graphviz graph. Reactions correspond to small green circles, and species to blue circles.

Notes:

  * Black arrows from species to reactions indicate reactants, and are labelled with their input stoichiometry.
  * Black arrows from reactions to species indicate products, and are labelled with their output stoichiometry.
  * Red arrows from species to reactions indicate that species is used within the rate expression. For example, in the reaction `k*A, B --> C`, there would be a red arrow from `A` to the reaction node. In `k*A, A+B --> C`, there would be red and black arrows from `A` to the reaction node.
  * Requires the Graphviz jll to be installed, or Graphviz to be installed and commandline accessible.
