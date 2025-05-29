```
HalfEdgeTopology(elements; sort=true)
HalfEdgeTopology(halfedges; nelems=nothing)
```

A data structure for orientable 2-manifolds based on half-edges constructed from a vector of connectivity `elements` or from a vector of pairs of `halfedges`.

The option `sort` can be used to sort the elements in adjacent-first order in case of inconsistent orientation (i.e. mix of clockwise and counter-clockwise).

The option `nelems` can be used to specify an approximate number of `elements` as a size hint.

## Examples

Construct half-edge topology from a list of top-faces:

```julia
elements = connect.([(1,2,3),(3,2,4,5)])
topology = HalfEdgeTopology(elements)
```

See also [`Topology`](@ref).

## References

  * Kettner, L. (1999). [Using generic programming for designing a data structure for polyhedral surfaces](https://www.sciencedirect.com/science/article/pii/S0925772199000073)

### Notes

Two types of half-edges exist (Kettner 1999). This implementation is the most common type that splits the incident elements.

A vector of `halfedges` together with a dictionary of `half4elem` and a dictionary of `half4vert` can be used to retrieve topolological relations in optimal time. In this case, `half4vert[i]` returns the index of the half-edge in `halfedges` with head equal to `i`. Similarly, `half4elem[i]` returns the index of a half-edge in `halfedges` that is in the element `i`. Additionally, a dictionary `edge4pair` returns the index of the edge (i.e. two halves) for a given pair of vertices.

If the `elements` of the mesh already have consistent orientation, then the `sort` option can be disabled for maximum performance.
