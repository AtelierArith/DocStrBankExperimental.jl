```
formulation(i::CombinatorialInstance, f::CombinatorialLinearFormulation)
```

この組合せインスタンスに対するLP定式化`f`を返します。2つの引数を返します：

  * JuMPモデル
  * 決定変数

`CombinatorialVariation`の場合、さらに3番目の引数として、`CombinatorialInstance`の上に`CombinatorialVariation`によってエンコードされた補足制約を返します。
