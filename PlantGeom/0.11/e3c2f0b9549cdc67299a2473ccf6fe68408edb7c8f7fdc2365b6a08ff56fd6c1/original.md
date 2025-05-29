```
merge_children_geometry!(mtg; from, into, delete=:nodes, verbose=true, child_link_fun=x -> new_child_link(x, verbose))
```

Simplifies the geometry of a MultiScaleTreeGraph (MTG) by merging low-scale geometries into an higher-scale geometry.

# Arguments

  * `mtg`: The MultiScaleTreeGraph to process.
  * `from`: The string for the type of nodes to simplify, this is the lower scale meshes that need to be merged. Can be a string or a vector of strings, *e.g.* ["Petiole", "Rachis"].
  * `into`: The string for the type of nodes to merge into. Must be a single string, *e.g.* "Leaf".
  * `delete`: A symbol indicating whether to delete the nodes or the geometry after merging:

      * `:none`: No deletion will be performed, the geometry is merged into the `into` nodes, and also kept as before in the `from` nodes.
      * `:nodes`: The nodes of type `from` will be deleted after merging.
      * `:geometry`: Only the geometry will be deleted, but the `from` nodes will remain in the MTG.
  * `verbose`: A boolean indicating if information should be returned when nodes or geometry was not found on expected nodes
  * `child_link_fun`: A function that takes a parent node targeted for deletion and returns the new links for their children. Required if `delete` is `true`. The

default function is `new_child_link`, which tries to be clever considering the parent and child links. See its help page for more information. If the link shouldn't be modified, use the `link` function instead.

# Returns

  * Nothing. The function modifies the `mtg` in place.

# Notes

If no geometry is found in the children nodes of type `from`, an informational message is logged.
