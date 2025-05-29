```
FacetIterator(gridordh::Union{Grid,AbstractDofHandler}, facetset::AbstractVecOrSet{FacetIndex})
```

Create a `FacetIterator` to conveniently iterate over the faces in `facestet`. The elements of the iterator are [`FacetCache`](@ref)s which are properly `reinit!`ialized. See [`FacetCache`](@ref) for more details.

Looping over a `FacetIterator`, i.e.:

```julia
for fc in FacetIterator(grid, facetset)
    # ...
end
```

is thus simply convenience for the following equivalent snippet: ```julia fc = FacetCache(grid) for faceindex in facetset     reinit!(fc, faceindex)     # ... end
