```
sectors(C::Commodity)
```

入力された商品が生産ブロックに含まれているセクターのみを返します。

これは、モデルを構築する際の最適化であり、構造が非常にスパースであるため、すべてのセクターを反復処理するのは高コストです。
