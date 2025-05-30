```
t8_geometry_linear_axis_aligned_new()
```

指定された次元の新しい線形、軸に整列したジオメトリを作成します。このジオメトリは、線/四角形/六角形要素にのみ適しており、ツリーごとに2つの頂点（最小および最大座標）を使用します。頂点は、t8*cmesh*set*tree*vertices関数を介して保存されます。

# 戻り値

t8*geometry*linear*axis*aligned () コンストラクタが呼び出されたかのように、割り当てられた t8*geometry*linear*axis*aligned 構造体へのポインタ。

### プロトタイプ

```c
t8_geometry_c * t8_geometry_linear_axis_aligned_new ();
```
