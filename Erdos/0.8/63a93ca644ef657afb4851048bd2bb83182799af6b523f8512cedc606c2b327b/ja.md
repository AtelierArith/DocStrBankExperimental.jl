```
weights(g)
```

エッジに関連付けられた「重み」を含むエッジマップを返します。単純グラフの場合、返される値は ConstEdgeMap(g, 1) です。ネットワークの場合、定義されている場合は「重み」エッジプロパティを返し、そうでない場合は定数マップを返します。

`weights` によって返されるエッジマップは、多くのフローおよびグラフアルゴリズムで使用されるエッジの重みのデフォルト値です。
