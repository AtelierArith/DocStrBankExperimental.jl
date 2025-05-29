```
Pxest{X,P,C} <: AbstractArray{P4estTypes.Tree,1}
```

Stores the forest of quadtrees (when `X=4`) or octrees (when `X=8`).

This forest of octrees can be accessed in two ways.  First, as an array-of-arrays. Each rank holds an array of quadrants for each tree of the [`Connectivity`](@ref) associated with the forest. (Note, the quadrants are distributed among the ranks. So, each rank will only have access to the quadrants it owns.) Second, using `iterateforest` to iterate over the volumes, faces, edges, and corners of the forest via callback functions.

# Fields

  * `pointer`: The pointer (of type `P`) can be a pointer to either a `P4estTypes.P4est.LibP4est.p4est` or a `P4estTypes.P4est.LibP4est.p8est`.  See the help documentation for these types for more information about the underlying p4est structures.
  * `connectivity`: The connectivity (of type `C`) the forest is associated with.  This is stored so the connectivity will not be reclaimed by the garbage collector too early.
  * `comm`: The MPI Communicator that includes the ranks participating in the forest.

# See also

  * [`pxest`](@ref): a function that constructs a `Pxest` from a [`Connectivity`](@ref).
  * [`iterateforest`](@ref): a function to iterate over the volumes, faces, edges, and corners of the forest.
  * [`refine!`](@ref): refine the quadrants of the forest.
  * [`coarsen!`](@ref): coarsen the quadrants of the forest.
  * [`balance!`](@ref): two-to-one balance the quadrants of the forest.
  * [`partition!`](@ref): partition the quadrants of the forest.
  * [`ghostlayer`](@ref): get the ghost layer of quadrants for the forest.
  * [`lnodes`](@ref): get a global node numbering.
  * [`P4estTypes.savevtk`](@ref): save a VTK representation of the forest.
