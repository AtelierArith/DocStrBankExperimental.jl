```
BOUNDARY(self::AbaqusExporter, NSET::AbstractString, dof::Integer,
  value::F) where {F}
```

ノードセットの非ゼロ値での変位を固定するための `*BOUNDARY` オプションを記述します。

  * `NSET` = ノードセット、
  * `dof` = 自由度、1, 2, 3
  * `typ` = 変位
