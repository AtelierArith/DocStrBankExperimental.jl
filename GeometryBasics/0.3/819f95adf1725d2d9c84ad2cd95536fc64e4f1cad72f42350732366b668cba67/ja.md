```
faces(contour::AbstractArray{Point}, [facetype = GLTriangleFace])
```

穴のない `AbstractArray{Point}` として与えられたポリゴンを三角形分割します。`contour` へのインデックスを定義する `Vector{facetype}` を返します。
