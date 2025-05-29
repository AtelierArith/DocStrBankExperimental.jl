```
FaceView(data, faces)
```

FaceViewは、頂点属性をメッシュに直接渡す代替手段です。これは、`data`を新しい`faces`のセットと束ねるもので、メッシュで定義された顔とは異なる方法でそのデータをインデックス付けすることができます。これは、`data`の重複を避けるのに役立ちます。

例えば、`data`は各面に対して一つの（繰り返しの）インデックスを与えることで、面ごとに定義できます：

```julia
per_face_normals = FaceView(
    normals,                 # 面ごとに1つ
    FT.(eachindex(normals))  # FT = facetype(mesh)を使用
)
```

レンダリングのために厳密に頂点ごとのデータが必要な場合は、`expand_faceviews(mesh)`を使用して、すべての頂点属性を頂点ごとに変換できます。これにより、データが重複し、必要に応じて面が再配置されます。

FaceViewのデータは`values(faceview)`で取得でき、面は`faces(faceview)`で取得できます。
