```
translate(oldPts::AbstractVector{XYPosition}, newPts::AbstractVector{XYPosition})::AffineMap
```

`oldPts`のX-Y座標を`newPts`のX-Y座標に変換するための最適なAffineMapを決定します。`oldPts`と`newPts`の座標は、同じ順序で同じ特徴を表すと仮定されているため、同じ数のX-Y座標を含む必要があります。
