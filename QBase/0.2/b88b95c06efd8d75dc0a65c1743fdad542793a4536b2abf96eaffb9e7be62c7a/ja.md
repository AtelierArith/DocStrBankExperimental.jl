```
n_product_id( tensor_coord :: Vector{Int64}, dims :: Vector{Int64} ) :: Int64
```

与えられたテンソル積の部分空間次元 `dims` とテンソル座標 `tensor_coord` に対して、クロネッカー積の対応する行列インデックスを返します。テンソル積 `dims` は、テンソル積内の各行列の次元を指定する正の定数整数のベクトルです。`tensor_coord` は、テンソル積内の各行列におけるターゲットインデックスを指定する正の定数整数のベクトルです。`dims` と `tensor_coord` は、テンソル積の行または列インデックスを記述する必要があります。

`tensor_coord` 内のいずれかのインデックスが無効である場合、または `tensor_coord` の要素数が `dims` の要素数と等しくない場合、`DomainError` がスローされます。
