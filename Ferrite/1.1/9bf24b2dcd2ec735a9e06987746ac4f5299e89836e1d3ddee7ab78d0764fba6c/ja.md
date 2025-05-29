```
geometric_interpolation(::AbstractCell)::ScalarInterpolation
geometric_interpolation(::Type{<:AbstractCell})::ScalarInterpolation
```

各 `AbstractCell` タイプは、そのジオメトリを記述するユニークな幾何学的補間を持っています。この関数は、その補間を返しますが、常にスカラー補間です。
