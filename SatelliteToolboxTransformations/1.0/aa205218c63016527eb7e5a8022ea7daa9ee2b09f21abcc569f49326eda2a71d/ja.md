```
ecef_to_ned(r_ecef::AbstractVector{T1}, lat::T2, lon::T3, h::T4; translate::Bool = false) -> SVector{3, T}
```

地球中心・地球固定（ECEF）フレームで表されたベクトル `r_ecef` を、測地的位置 `lat` [rad]、`lon` [rad]、および `h` [m] におけるローカル参照フレーム NED（北、東、下）に変換します。

`translate` が `false` の場合、この関数は ECEF と NED の間の回転のみを計算します。それ以外の場合、地球の中心と NED 原点との距離を考慮してベクトルを平行移動します。

返されるベクトルの要素型 `T` は、`T1`、`T2`、`T3`、および `T4` を浮動小数点数に昇格させることによって得られます。

# 備考

このアルゴリズムは **[1]** の情報に基づいています。

# 参考文献

  * **[1]**: [Transformations between ECEF and ENU   coordinates](https://gssc.esa.int/navipedia/index.php/Transformations_between_ECEF_and_ENU_coordinates)

```
