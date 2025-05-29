```
BOUNDARY(self::AbaqusExporter, mesh, nodes, is_fixed::AbstractArray{B,2}, fixed_value::AbstractArray{F,2}) where {B, F}
```

`*BOUNDARY`オプションを記述します。

境界条件は、配列`nodes`で指定されたノードに適用され、メッシュ（またはノードセット）`meshornset`に適用されます。

`meshornset` = メッシュまたはノードセット（デフォルトは空） `nodes` = ノード番号の配列、ノード番号はメッシュラベルに付随しています、`is_fixed`= ブールフラグの配列（trueは固定または指定されたことを意味します）、ノードごとに1行、`fixed_value`= 対応する変位成分が固定される変位の配列

# 例

```
BOUNDARY(AE, "ASSEM1.INSTNC1", 1:4, fill(true, 4, 1), reshape([uy(fens.xyz[i, :]...) for i in 1:4], 4, 1))
```
