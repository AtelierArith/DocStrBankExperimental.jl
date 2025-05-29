```
map_interpolate(mapS::Union{MapS,MapSd,MapS3D}, type::Symbol = :cubic;
                return_vert_deriv::Bool = false)
```

マップ補間関数を作成します。これはMATLABのgriddedInterpolantに相当します。オプションで、マップと1 m上方に続くマップとの間の有限差分を使用して計算される垂直導関数マップ補間関数を返します。

**引数:**

  * `mapS`:              `MapS`、`MapSd`、または`MapS3D`スカラー磁気異常マップ構造体
  * `type`:              （オプション）補間のタイプ {:linear,:quad,:cubic}
  * `return_vert_deriv`: （オプション）trueの場合、`der_map`も返します

**戻り値:**

  * `itp_map`: マップ補間関数 (`f(yy,xx)` または (`f(yy,xx,alt)`)
  * `der_map`: `return_vert_deriv = true`の場合、垂直導関数マップ補間関数 (`f(yy,xx)` または (`f(yy,xx,alt)`)
