```
struct FGVertex
```

`FlipGraph`の*頂点*。

`FGVertex`は、その頂点の同変類の表現（`DeltaComplex`）で構成されています。表現は、*McKayのアルゴリズム*の適応によって得られた標準的なラベリングの1つで再ラベリングされています。さらに、`FGVertex`には、それぞれの*McKayのアルゴリズム*によって出力されるラベリングの数が含まれています。
