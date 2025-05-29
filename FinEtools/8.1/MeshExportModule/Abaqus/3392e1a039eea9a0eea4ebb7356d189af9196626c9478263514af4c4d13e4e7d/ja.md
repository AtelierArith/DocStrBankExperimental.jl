```
BOUNDARY(self::AbaqusExporter, meshornset, is_fixed::AbstractArray{B,2}, fixed_value::AbstractArray{F,2}) where {B, F}
```

`*BOUNDARY`オプションを記述します。

  * `meshornset` = メッシュまたはノードセットの名前、
  * `is_fixed`= ブールフラグの配列（trueは固定または指定されたことを意味します）、ノードごとに1行、ノードごとの自由度の数だけの列、
  * `fixed_value`= 対応する変位成分が固定される変位の配列、ノードごとの自由度の数だけの列
