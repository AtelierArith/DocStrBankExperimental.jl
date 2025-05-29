```
C = griddata(A::ClimGrid, londest::AbstractArray{N, 1} where N, latdest::AbstractArray{N, 1} where N)
```

`ClimGrid` Aをlondestおよびlatdestベクトルまたは配列で定義された緯度経度グリッドに補間します。配列が提供される場合、グリッドは曲線的であると見なされ（通常の緯度経度グリッドではなく）、ユーザーはそのようなグリッドの次元ベクトル（"x"および"y"）を提供する必要があります。
