```
t8_geom_linear_interpolation(coefficients, corner_values, corner_value_dim, interpolation_dim, evaluated_function)
```

2点間で線形補間を行い、4点間で双線形補間を行い、8点間で三線形補間を行います。

# 引数

  * `coefficients`:[in] 補間に使用される係数のサイズが少なくともdimの配列
  * `corner_values`:[in] 単位正方形/立方体の各コーナー（zorderで）の空間における関数値を与えるサイズ2^dim * 3の配列。
  * `corner_value_dim`:[in] *corner_values*の次元。
  * `interpolation_dim`:[in] 補間の次元（線形の場合は1、双線形の場合は2、三線形の場合は3）
  * `evaluated_function`:[out] サイズ*corner*value*dim*の配列で、出力として補間の結果が得られます。

### プロトタイプ

```c
void t8_geom_linear_interpolation (const double *coefficients, const double *corner_values, int corner_value_dim, int interpolation_dim, double *evaluated_function);
```
