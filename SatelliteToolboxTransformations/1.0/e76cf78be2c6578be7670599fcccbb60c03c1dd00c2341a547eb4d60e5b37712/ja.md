```
r_ecef_to_ecef([T, ]ECEFo, ECEFf, jd_utc::Number, eop) -> T
```

地球中心・地球固定（ECEF）基準フレーム `ECEFo` から別の ECEF 基準フレーム `ECEFf` への回転を、ユリウス日 `jd_utc` [UTC] において計算します。使用される回転の記述は `T` によって与えられ、`DCM` または `Quaternion` である可能性があります。このアルゴリズムは、地球の姿勢パラメータ（EOP） `eop` も必要とします。

!!! note
    より詳しい情報、特に起点と目的の基準フレームを指定する方法については、**拡張ヘルプ**を参照してください。


# 戻り値

  * `T`: ユリウス日 `jd_utc` において `ECEFo` 基準フレームを `ECEFf` 基準フレームに整合させる回転エンティティ。

# 拡張ヘルプ

## 回転の記述

回転は方向余弦行列（DCM）またはクォータニオンで記述できます。これはパラメータ `T` によって選択されます。可能な値は次のとおりです。

  * `DCM`: 回転は方向余弦行列によって記述されます。
  * `Quaternion`: 回転はクォータニオンによって記述されます。

値が指定されていない場合は、`DCM` にフォールバックします。

## 変換モデル

回転を計算するために使用されるモデルは、起点と目的のフレームの選択に基づいて自動的に推測されます。**IAU-76/FK5 と IAU-2006/2010 フレームを混合することはサポートされていません。**

## サポートされている ECEF 基準フレーム

起点 `ECEFo` と目的 `ECEFf` の両方に対してサポートされている ECEF フレームは次のとおりです。

  * `ITRF()`: ECEF は国際地球基準フレーム（ITRF）として選択されます。
  * `PEF()`: ECEF は擬似地球固定（PEF）基準フレーム（IAU-76/FK5）として選択されます。
  * `TIRS()`: ECEF は地球中間基準系（TIRS）（IAU-2006/2010）として選択されます。

## 地球の姿勢パラメータ（EOP）

サポートされている ECEF フレーム間の変換は **常に** EOP に依存します（[`fetch_iers_eop`](@ref) および [`read_iers_eop`](@ref] を参照）。IAU-76/FK5 モデルが使用される場合、`eop` の型は [`EopIau1980`](@ref) でなければなりません。そうでない場合、IAU-2006/2010 モデルが使用される場合、`eop` の型は [`EopIau2000A`](@ref) でなければなりません。

## 例

```julia-repl
julia> eop_iau1980 = fetch_iers_eop();

julia> r_ecef_to_ecef(PEF(), ITRF(), date_to_jd(1986, 6, 19, 21, 35, 0), eop_iau1980)
DCM{Float64}:
  1.0          0.0         -4.34677e-7
 -6.29476e-13  1.0         -1.44815e-6
  4.34677e-7   1.44815e-6   1.0

julia> r_ecef_to_ecef(Quaternion, PEF(), ITRF(), date_to_jd(1986, 6, 19, 21, 35, 0), eop_iau1980)
Quaternion{Float64}:
  + 1.0 - 7.24073e-7⋅i + 2.17339e-7⋅j - 0.0⋅k

julia> eop_iau2000A = fetch_iers_eop(Val(:IAU2000A));

julia> r_ecef_to_ecef(TIRS(), ITRF(), date_to_jd(1986, 6, 19, 21, 35, 0), eop_iau2000A)
DCM{Float64}:
  1.0          3.08408e-11  -4.34677e-7
 -3.14703e-11  1.0          -1.44815e-6
  4.34677e-7   1.44815e-6    1.0

julia> r_ecef_to_ecef(Quaternion, TIRS(), ITRF(), date_to_jd(1986, 6, 19, 21, 35, 0), eop_iau2000A)
Quaternion{Float64}:
  + 1.0 - 7.24073e-7⋅i + 2.17339e-7⋅j + 1.55778e-11⋅k
```
