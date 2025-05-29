```
grot!(geo::GenericTrace, ang::Real, axis::Vector{<:Real}, origin::Vector{<:Real}=[0])

指定された角度 `ang` で、軸 `axis` と原点 `origin` の周りにジオメトリを回転させます。

# 引数
- `geo::GenericTrace`: 回転させるジオメトリ。
- `ang::Real`: 回転角度。
- `axis::Vector{<:Real}`: 回転軸。
- `origin::Vector{<:Real}=[0]`: 回転の原点。指定されていない場合はジオメトリの中心がデフォルトとなります。
```
