```
addBackgroundGrid!(proj::Project, x0::Array{Float64}, dx::Array{Float64}, N::Array{Int})
```

Add the background grid block using the left corner, x0, the grid size dx, and the number of intervals in each direction. Use this when there is *no* outer boundary defined in the model. This version mimics HOHQMesh's backgroundGrid block, but the version

```
addBackgroundGrid!(proj::Project, box::Array{Float64},  N::Array{Int} )
```

is a lot easier to use.

TODO: Change HOHQMesh and delete this way to specify the domain and use the bounding box one instead.
