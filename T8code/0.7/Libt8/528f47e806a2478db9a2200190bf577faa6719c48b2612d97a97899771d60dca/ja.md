```
t8_line_point_inside(p_0, vec, point, tolerance)
```

始点 *p_0* とベクトル *vec* で定義された直線内に点があるかどうかを確認します。

# 引数

  * `p_0`:[in] 直線の始点
  * `vec`:[in] 直線の方向（正規化されていない）
  * `point`:[in] チェックする点の座標
  * `tolerance`:[in] 許容範囲を定義する 0 より大きい倍精度浮動小数点数

# 戻り値

点が外側にある場合は 0、そうでない場合は 1 を返します。

### プロトタイプ

```c
int t8_line_point_inside (const double *p_0, const double *vec, const double *point, const double tolerance);
```
