```
faces(contour::AbstractArray{Point}, [facetype = GLTriangleFace])
```

Triangulates a Polygon given as an `AbstractArray{Point}` without holes. It will return a Vector{`facetype`}, defining indexes into `contour`
