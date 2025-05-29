TernaryContourf

バリセンター座標 `x`, `y`, `z` を使用して塗りつぶされた等高線プロットを描画します。すなわち、`x + y + z = 1` です。座標の重みは `w` を通じて渡されます。

## ノート

データは常にパディングされ、プロット領域全体を塗りつぶすのが容易になります。パディングされたデータは、最も近いデータポイントに基づいて補間されます。

## 属性

`MakieCore.Plot{TernaryDiagrams.ternarycontourf}` の利用可能な属性とそのデフォルトは次のとおりです：

```
  colormap  :Spectral
  levels    5
```
