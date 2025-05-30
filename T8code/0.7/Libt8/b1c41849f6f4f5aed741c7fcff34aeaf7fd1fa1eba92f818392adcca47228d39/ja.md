```
t8_element_vertex_reference_coords(ts, t, vertex, coords)
```

与えられた要素の頂点の座標を、[0,1]^d (d = 次元) に埋め込まれた参照ツリー内で計算します。

!!! warning
    coordsはゼロ初期化されている必要があります。最初のd個の座標のみが設定されますが、他の場所で使用されるとすべての座標が使用される可能性があります。


# 引数

  * `t`:[in] 考慮される要素。
  * `vertex`:[in] 座標を計算する頂点のID。
  * `coords`:[out] 要素の次元と同じ数以上の倍精度浮動小数点数の配列で、*vertex*の座標で埋められます。

### プロトタイプ

```c
void t8_element_vertex_reference_coords (const t8_eclass_scheme_c *ts, const t8_element_t *t, const int vertex, double coords[]);
```
