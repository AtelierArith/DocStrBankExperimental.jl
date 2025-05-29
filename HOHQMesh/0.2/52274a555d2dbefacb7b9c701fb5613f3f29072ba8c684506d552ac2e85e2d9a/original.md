```
addBackgroundGrid!(proj::Project, box::Array{Float64},  N::Array{Int} )
```

Add the background grid block with bounding box = [TOP, LEFT, BOTTOM, RIGHT] and the number of intervals in each diredction. Use this when there is *no* outer boundary defined in the model.
