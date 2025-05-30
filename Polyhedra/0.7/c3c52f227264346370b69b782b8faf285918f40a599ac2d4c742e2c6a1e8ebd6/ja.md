```
isredundant(p::Rep, idx::Index; strongly=false)
```

`idx`のインデックスを持つ要素が`p`によって表される多面体を変更することなく削除できるかどうかを示す`Bool`を返します。`strongly`が`true`の場合、

  * `idx`がH-表現要素`h`である場合、`h`の超平面に`p`のV-表現要素が存在しない場合にのみ`true`を返します。
  * `idx`がV-表現要素`v`である場合、`v`が`p`の相対内部にある場合にのみ`true`を返します。
