```
T4blockx(xs::VecOrMat{T}, ys::VecOrMat{T}, zs::VecOrMat{T}, orientation::Symbol = :a) where {T<:Number}
```

Generate a graded tetrahedral mesh  of a 3D block.

Four-node tetrahedra in a regular arrangement, with non-uniform given spacing between the nodes, with a given orientation of the diagonals.

The mesh is produced by splitting each logical  rectangular cell into five or six tetrahedra: refer to `T4block`.
