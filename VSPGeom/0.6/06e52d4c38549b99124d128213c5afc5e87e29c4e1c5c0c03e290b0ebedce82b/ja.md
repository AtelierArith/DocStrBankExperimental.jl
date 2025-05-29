```
TriMesh(name::String)
```

  * `name::String`: 名前
  * `ncells::Int`: セルの数
  * `normals::Vector{Vector{Float64}}`: 各セルの法線のベクトル
  * `zeroBased::Vector{Bool}`: true の場合、接続情報のインデックスはゼロベースのインデックスです。可変にするためのベクトル。
  * `points::Vector{Vector{Float64}}`: ユニークなポイントのベクトル
  * `cells::Vector{Vector{Int}}`: `points` のインデックスとしての各セルの頂点のベクトル
