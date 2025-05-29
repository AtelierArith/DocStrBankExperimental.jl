```
rot!(geo::Geometry, ang::Real, axis::Vector{<:Real}, origin::Vector{<:Real}=[0]; render=false)

指定された角度 `ang` で、軸 `axis` と原点 `origin` の周りに幾何学を回転させます。

# 引数
- `geo::Geometry`: 回転させる幾何学。
- `ang::Real`: 回転角度。
- `axis::Vector{<:Real}`: 回転軸。
- `origin::Vector{<:Real}=[0]`: 回転の原点。指定されていない場合は幾何学の中心がデフォルトとなります。

# キーワード
- `render=false`: 作成/操作のためのリアルタイムレンダリング。
```
