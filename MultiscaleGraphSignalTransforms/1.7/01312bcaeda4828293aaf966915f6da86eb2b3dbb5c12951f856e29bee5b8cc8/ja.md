```
levlist2levlengths!(GP::GraphPart, BS::BasisSpec)
```

BasisSpecオブジェクトのlevlengths情報を計算します

### 入力引数

  * `GP::GraphPart`: GraphPartオブジェクト
  * `BS::BasisSpec`: `levlengths`を持たないBasisSpecオブジェクト; この関数の後、`levlengths`フィールドが填充されます。
