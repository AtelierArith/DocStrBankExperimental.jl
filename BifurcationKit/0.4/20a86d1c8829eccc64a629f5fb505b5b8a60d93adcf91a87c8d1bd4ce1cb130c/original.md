Structure to hold a connected component of a bifurcation diagram.

## Fields

  * `level::Int64`: current recursion level
  * `code::Int64`: code for finding the current node in the tree, this is the index of the bifurcation point from which γ branches off
  * `γ::Any`: branch associated to the current node
  * `child::Any`: children of current node. These are the different branches off the bifurcation point in γ

## Methods

  * `hasbranch(diagram)`
  * `from(diagram)`
  * `diagram[code]` For example `diagram[1,2,3]` returns `diagram.child[1].child[2].child[3]`
