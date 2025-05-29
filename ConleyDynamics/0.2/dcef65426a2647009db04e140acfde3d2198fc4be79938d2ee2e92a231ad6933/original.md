```
create_mvf_hull(lc::LefschetzComplex, mvfbase::Vector{Vector{Int}})
```

Create the smallest multivector field containing the given sets.

The resulting multivector field has the property that every set of the form `mvfbase[k]` is contained in a minimal multivector. Notice that these sets do not have to be disjoint, and that not even their locally closed hulls have to be disjoint. In the latter case, this leads to two such sets having to be contained in the same multivector. If the sets in `mvfbase` are poorly chosen, one might end up with extremely large multivectors due to the above potential merging of locally closed hulls.
