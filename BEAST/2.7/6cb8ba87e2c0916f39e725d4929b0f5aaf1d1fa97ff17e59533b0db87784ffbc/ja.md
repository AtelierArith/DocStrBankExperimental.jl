```
ntrace(refspace, element, localindex, face)
```

`refspace`に属する`elements`上の`face`でのすべての局所形状関数の法線トレースを計算します。この関数は、`refspace`内の局所形状関数のトレースを局所トレース空間の関数の線形結合として表現する行列を返します。Cf. `restrict`。`localindex`は、`elements`の面の列挙における`face`のインデックスです。このインデックスを知ることで、多くの特別なケースで高度に最適化された実装が可能になります。
