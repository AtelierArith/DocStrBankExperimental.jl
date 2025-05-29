```
t8_geometry_lagrange_destroy(geom)
```

Lagrangeジオメトリを破棄します。これは、t8*geometry*lagrange_newで作成されたものです。

# 引数

  * `geom`:[in,out] Lagrangeジオメトリ。出力時にNULLに設定されます。

### プロトタイプ

```c
void t8_geometry_lagrange_destroy (t8_geometry_c **geom);
```
