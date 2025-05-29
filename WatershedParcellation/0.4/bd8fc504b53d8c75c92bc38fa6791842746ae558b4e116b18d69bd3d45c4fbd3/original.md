```
remove_articulation_points!(px; threshold)
```

If any parcels in `px::Parcellation` have an articulation point or cut vertex, the removal of which will disconnect the parcel, then remove that vertex and  separate the parcel into its resulting connected components, as long as there are at least two "reasonably sized" components of size >= `minsize` vertices.

Returns the number of articulation points that were handled.
