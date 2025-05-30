```
t8_geom_triangular_interpolation(coefficients, corner_values, corner_value_dim, interpolation_dim, evaluated_function)
```

3点（三角形）または4点（四面体）間の三角補間を直交座標を使用して行います。入力係数は、参照三角形（interpolation*dim = 2）の座標として、点 (0,0) (1,0) (1,1) または参照四面体（interpolation*dim = 3）の座標として、点 (0,0,0) (1,0,0) (1,1,0) (1,1,1) として与える必要があります。

# 引数

  * `coefficients`:[in] 補間に使用される参照三角形/四面体の係数を与える *interpolation_dim* サイズの配列
  * `corner_values`:[in] 各コーナーの三角形/四面体の関数値を与える 3 * *corner*value*dim* サイズの配列（*interpolation_dim* == 2 の場合）または 4 * *corner*value*dim* サイズの配列（*interpolation_dim* == 3 の場合）、（zorderで）
  * `corner_value_dim`:[in] *corner_values* の次元。
  * `interpolation_dim`:[in] 補間の次元（三角形の場合は2、四面体の場合は3）
  * `evaluated_function`:[out] *corner*value*dim* サイズの配列、出力として補間の結果。

### プロトタイプ

```c
void t8_geom_triangular_interpolation (const double *coefficients, const double *corner_values, int corner_value_dim, int interpolation_dim, double *evaluated_function);
```
