```
Mesh(faces[; views, attributes...])
Mesh(positions, faces[; views])
Mesh(positions, faces::AbstractVector{<: Integer}[; facetype = TriangleFace, skip = 1])
Mesh(; attributes...)
```

与えられた引数からメッシュを構築します。

`positions` が明示的に与えられている場合、それらは `position` という名前の他の頂点属性とマージされます。そうでない場合、それらは `attributes` の一部でなければなりません。`faces` が与えられていない場合、`attributes.position` は FaceView でなければなりません。

他のすべての頂点属性は、`AbstractVector` またはその `FaceView` である必要があります。`AbstractVector` であるすべての頂点属性は、`mesh.faces` によってインデックス可能であるために十分な大きさでなければなりません。`FaceView` であるすべての頂点属性は、`mesh.faces` と類似の面を含む必要があります。つまり、同じ数の面を含み、面の長さが一致している必要があります。

`views` はオプションで定義でき、メッシュを複数のサブメッシュに暗黙的に分割します。これは、サブメッシュに対応する面のインデックス付けのための範囲を提供することによって行われます。デフォルトでは、これは空のままにされます。
