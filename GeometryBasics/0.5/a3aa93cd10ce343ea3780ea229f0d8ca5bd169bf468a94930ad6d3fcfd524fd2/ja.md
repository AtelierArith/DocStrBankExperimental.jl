```
normals(positions::Vector{Point3{T}}, faces::Vector{<: NgonFace}[; normaltype = Vec3{T}])
```

与えられた `positions` と `faces` から頂点法線を計算します。

これはすべての面を通過し、各面法線を計算して、関与するすべての頂点に追加します。面法線の方向は巻き方向に基づいており、反時計回りの面が仮定されています。最後に、合計された面法線は再度正規化されて、頂点法線が生成されます。
