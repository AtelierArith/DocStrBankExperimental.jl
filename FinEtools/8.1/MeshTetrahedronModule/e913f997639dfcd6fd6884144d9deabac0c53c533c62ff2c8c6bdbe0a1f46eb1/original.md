```
T10blockx(xs::VecOrMat{T}, ys::VecOrMat{T}, zs::VecOrMat{T}, orientation::Symbol = :a) where {T<:Number}
```

Generate a graded 10-node tetrahedral mesh  of a 3D block.

10-node tetrahedra in a regular arrangement, with non-uniform given spacing between the nodes, with a given orientation of the diagonals.

The mesh is produced by splitting each logical  rectangular cell into six tetrahedra.
