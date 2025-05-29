```
GeneralLattice{D,K,T} <: AbstractLattice{D}
GeneralLattice(vectors, sites)
```

空間をタイルするための一般的な格子型。型パラメータ `D` は次元、`K` は単位セル内のサイトの数、`T` は座標のデータ型、例えば `Float64` です。入力引数は次の通りです。

  * `vectors` は D-タプルのベクトル/タプルです。その長さは D で、ブラヴェ格子ベクトルを指定します。
  * `sites` は D-タプルのベクトル/タプルです。その長さは K で、ブラヴェセル内のサイトを指定します。
