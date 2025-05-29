```
GeometricProperties
```

構造物の主および副の幾何学的特性を微分可能な形式で取得します。

フィールド:

  * X: すべてのノードのx位置
  * Y: すべてのノードのy位置
  * Z: すべてのノードのz位置
  * evecs: [nel × 3] 行列で、row_i = nodes[iend].position - nodes[istart].position
  * A: すべての要素の面積
  * L: すべての要素の長さ

```

```
