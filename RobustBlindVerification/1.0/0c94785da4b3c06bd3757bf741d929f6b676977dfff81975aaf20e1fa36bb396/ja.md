````
MBQCAngles(angles) 

- グラフに関連する角度を表す構造体。角度の数はグラフの頂点の数と同じになります。

# パラメータ
- `angles`: 頂点と同じ方法でインデックス可能な値のリストセット。

# 例
```
julia> angles = [π,π/4,5π/4,7π/4]
julia> mbqc_angles = MBQCAngles(angles) 
```
````
