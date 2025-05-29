カメラインタリンズのピクセルからカメラスペースへの投影。

投影は次のように行われます：`((x, y) .- principal) ./ focal`。その後、歪みがある場合は補正が行われます。

# 引数：

  * `distortion::Maybe{SVector{4, Float32}}`：歪みがない場合は`nothing`。
  * `focal::SVector{2, Float32}`：焦点距離は`(fx, fy)`形式。
  * `principal::SVector{2, Float32}`：主点は`(cx, cy)`形式。`resolution`（`[0, 1]`範囲内）で正規化されています。
  * `resolution::SVector{2, UInt32}`：解像度は`(width, height)`形式。
