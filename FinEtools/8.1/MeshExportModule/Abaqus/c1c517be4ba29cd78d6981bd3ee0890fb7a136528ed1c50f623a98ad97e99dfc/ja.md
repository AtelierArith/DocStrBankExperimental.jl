```
BOUNDARY(self::AbaqusExporter, NSET::AbstractString, dof::Integer,  fixed_value)
```

`*BOUNDARY`オプションを記述します。

  * `NSET` = ノードセットの名前、
  * `is_fixed`= ブールフラグの配列（trueは固定または指定されたことを意味します）、ノードごとに1行、
  * `fixed_value`= 対応する変位成分が固定される変位の配列
