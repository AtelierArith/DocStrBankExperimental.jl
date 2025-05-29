```
ned_to_ecef(r_ned::AbstractVector{T1}, lat::T2, lon::T3, h::T4; translate::Bool = false) -> SVector{3, T}
```

ローカル基準フレームNED（北、東、下）で表されたベクトル`r_ned`を、測地的位置`lat` [rad]、`lon` [rad]、および`h` [m]において、地球中心・地球固定（ECEF）フレームに変換します。

`translate`が`false`の場合、この関数はNEDとECEFの間の回転のみを計算します。それ以外の場合、地球の中心とNEDの原点との距離を考慮してベクトルを平行移動します。

返されるベクトルの要素型`T`は、`T1`、`T2`、`T3`、および`T4`を浮動小数点数に昇格させることによって得られます。

# 備考

このアルゴリズムは**[1]**の情報に基づいています。

# 参考文献

  * **[1]** [Transformations between ECEF and ENU   coordinates](https://gssc.esa.int/navipedia/index.php/Transformations_between_ECEF_and_ENU_coordinates)

```
