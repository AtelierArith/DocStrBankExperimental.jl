```
t8_geometry_linear_axis_aligned_new()
```

与えられた次元の新しい線形、軸に整列したジオメトリを作成します。このジオメトリは、線/四角/六角要素にのみ適しており、ツリーごとに2つの頂点（最小および最大座標）を使用します。頂点は、t8*cmesh*set*tree*vertices関数を介して保存されます。

# 戻り値

t8*geometry*linear*axis*aligned構造体へのポインタが返されます。これは、t8*geometry*linear*axis*aligned()コンストラクタが呼び出されたかのようです。

### プロトタイプ

```c
t8_geometry_c * t8_geometry_linear_axis_aligned_new ();
```
