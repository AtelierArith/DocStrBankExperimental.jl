```
t8_triangle_point_inside(p_0, v, w, point, tolerance)
```

点 *p_0* と二つのベクトル *v* と *w* で表される三角形の内部に点があるかどうかを確認します。

# 引数

  * `p_0`:[in] 三角形の最初の頂点
  * `v`:[in] p*0 から p*1 へのベクトル（三角形の第二の頂点）
  * `w`:[in] p*0 から p*2 へのベクトル（三角形の第三の頂点）
  * `point`:[in] 確認する点の座標
  * `tolerance`:[in] 許容範囲を定義する 0 より大きい倍精度浮動小数点数

# 戻り値

点が外側にある場合は 0、そうでない場合は 1。

### プロトタイプ

```c
int t8_triangle_point_inside (const double p_0[3], const double v[3], const double w[3], const double point[3], const double tolerance);
```
