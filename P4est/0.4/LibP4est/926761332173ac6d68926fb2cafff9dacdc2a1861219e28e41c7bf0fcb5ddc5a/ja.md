```
p8est_iter_edge_info
```

森のエッジのすべての側面に関する情報。tree*boundaryがfalseの場合、エッジは木の内部にあります。tree*boundaryがfalseの場合、sides[0]にはエッジに接触する最も低いz-orderの四分円が含まれます。tree*boundaryがtrueの場合、その値はエッジの木に対する位置に応じてP8EST*CONNECT_FACE/EDGEになります。

| フィールド         | 注釈                            |
|:------------- |:----------------------------- |
| tree_boundary | boolean: 内部面 (0)、木の境界面 (true) |
| sides         | `p8est_iter_edge_side_t`型の配列  |
