```
get_angle(resource::MBQCResourceState, AngleType, vertex)
```

指定された `MBQCResourceState` と `AngleType` から特定の頂点の角度を返します。

# 引数

  * `resource`: 角度を抽出する `MBQCResourceState`。
  * `AngleType`: 抽出する角度のタイプ。
  * `vertex`: 角度を抽出する頂点。

# 例

```julia
angle = get_angle(resource, SecretAngles(), vertex) # 指定された頂点の角度を返します
```
