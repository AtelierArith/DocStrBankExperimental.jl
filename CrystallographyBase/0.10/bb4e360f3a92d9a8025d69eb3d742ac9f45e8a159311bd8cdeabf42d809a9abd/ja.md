```
crystaldensity(lattice::Lattice, atoms)
crystaldensity(cell::Cell)
```

結晶構造の密度を計算します。

ここで、`atoms`は原子番号、元素名、記号、または`Mendeleev.Element`の反復可能な集合です。カスタムタイプで動作するように`atomicmass`メソッドを拡張できます。
