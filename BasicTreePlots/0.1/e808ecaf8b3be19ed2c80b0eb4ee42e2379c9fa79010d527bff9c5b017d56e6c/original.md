```
treeplot(tree; kwargs...)
```

# Args:

  * tree, the root node of a tree that has `AbstractTrees.children()` defined.   All nodes should be reachable by using `AbstractTrees.PreOrderDFS()` iterator.

# Keyword arguments:

  * `showroot::Bool = false`, if `BasicTreePlots.distance()` is not `nan` for root, show line linking root to parent.
  * `layoutstyle::Symbol = :dendrogram` available options are `:dendrogram`, or `:cladogram`

      * `:dendrogram` displays tree taking into account the distance between parent and children nodes as calculated from `BasicTreePlots.distance(node)`.   If the distance is not defined, it defaults to `1` and is equivalent to the `:cladogram` layout
      * `:cladogram` displays the tree where each distance from a child node to their parent is set to `1`.
  * `branchstyle::Symbol = :square` available options are `:square` or `:straight`

      * `:square` will display line from child to parent as going back to the height of the parent,   before connecting back to the parent node at a right angle.
      * `straight` will display line from child to parent as a straight line from child to parent.
  * `linecolor = :black`, should match the `color` option in Makie's `lines` plot.   Can be either a single color `:black`, color plus alpha transperency `(:black, 0.5)`, or a vector of numbers for each node in pre-walk order.   color for each node is associated to the line connecting it to its parent.
  * `linewidth = 1`, should match the `linewidth` option in Makie's `lines` plot.   Can be either a single width or a vector of numbers for each node in pre-walk order.   width for each node is associated to the line connecting it to its parent.
  * `linecolormap=:viridis`  color map associated to `linecolor`. can be symbel of known colormap or gradient created from `cgrad()`.   see [Makie's color documentation](https://docs.makie.org/v0.21/explanations/colors)
  * `branch_point_resolution = 25`, number of points associated to each line segment.   Can be decreased to increase plotting speed.   Or, increased if lines that should be smooth are not.
  * `usemaxdepth = false`, if `true` draw guide lines from each leaf tip to the depth of the leaf that is maximally distant from root.   Useful for connecting leaves to there location on the y axis (or θ axis if plotted on `PolarAxis`).
  * `tipannotationsvisible::Bool = true`, whether to show text labels for each leaf tip.
  * `tipfontsize = 9.0f0`, font size that tip labels are displayed at.
  * `openangle = 0`, Angle in radians that limits span of tree around the circle when plotted on `PolarAxis`.   if `openangle = deg2rad(5)` then leaf tips will spread across angles `0` to `(2π - openangle)`.
  * `tipalign = (:left, :center)` text alignment of tip labels.   see [Makie options](https://docs.makie.org/v0.21/reference/plots/text#alignment)
  * `tipannotationoffset = (3.0f0, 0.0f0)` offset of tip label from actual tip position.   The first value is associated with the `x` axis, and the second is associated with the `y` axis.   (Currently, only available for cartisian axis)
