```
r_eci_to_ecef([T, ]ECI, ECEF, jd_utc::Number[, eop]) -> T
```

地球中心慣性（`ECI`）参照フレームから地球中心固定（`ECEF`）参照フレームへの回転を、ユリウス日 `jd_utc` [UTC] において計算します。使用される回転の記述は `T` によって与えられ、`DCM` または `Quaternion` である可能性があります。アルゴリズムは、ソースフレームと宛先フレームに応じて、地球の姿勢パラメータ（EOP） `eop` を必要とする場合があります。

!!! note
    より詳しい情報、特に起点と宛先の参照フレームを指定する方法については、**拡張ヘルプ**を参照してください。


# 戻り値

  * `T`: ECI参照フレームをECEF参照フレームに整列させる回転エンティティ。

# 拡張ヘルプ

## 回転の記述

回転は方向余弦行列（DCM）またはクォータニオンで記述できます。これはパラメータ `T` によって選択されます。可能な値は次のとおりです。

  * `DCM`: 回転は方向余弦行列によって記述されます。
  * `Quaternion`: 回転はクォータニオンによって記述されます。

値が指定されていない場合は、`DCM` にフォールバックします。

## 変換モデル

回転を計算するために使用されるモデルは、起点と宛先のフレームの選択に基づいて自動的に推測されます。**IAU-76/FK5 と IAU-2006/2010 フレームを混合することはサポートされていません。**

## サポートされている ECI 参照フレーム

ECI フレームはパラメータ `ECI` によって選択されます。可能な値は次のとおりです。

  * `TEME()`: ECI は真の赤道平均春分点（TEME）参照フレームとして選択されます。
  * `TOD()`: ECI は日付の真の（TOD）として選択されます。
  * `MOD()`: ECI は日付の平均（MOD）として選択されます。
  * `J2000()`: ECI は J2000 参照フレームとして選択されます。
  * `GCRF()`: ECI は地心天体参照フレーム（GCRF）として選択されます。
  * `CIRS()`: ECEF は天体中間参照系（CIRS）として選択されます。
  * `ERS()`: ECI は地球参照系（ERS）として選択されます。
  * `MOD06()`: ECI はIAU-2006/2010理論の定義に従って日付の平均（MOD）として選択されます。
  * `MJ2000()`: ECI は J2000 平均赤道フレーム（MJ2000）として選択されます。

!!! note
    フレーム `MOD()` と `MOD06()` は実質的に同じです。ただし、IAU-76/FK5 と IAU-2006/2010 のフレーム間の変換を混合する際には注意が必要であることを明確にするために、異なる名前を選択しました。


## サポートされている ECEF 参照フレーム

ECEF フレームはパラメータ `ECEF` によって選択されます。可能な値は次のとおりです。

  * `ITRF()`: ECEF は国際地球参照フレーム（ITRF）として選択されます。
  * `PEF()`: ECEF は擬似地球固定（PEF）参照フレームとして選択されます。
  * `TIRS()`: ECEF は地球中間参照系（TIRS）として選択されます。

## 地球の姿勢パラメータ（EOP）

フレーム間の変換は EOP に依存する場合があります（[`fetch_iers_eop`](@ref) および [`read_iers_eop`](@ref) を参照）。IAU-76/FK5 モデルが使用される場合、`eop` の型は [`EopIau1980`](@ref) でなければなりません。そうでない場合、IAU-2006/2010 モデルが使用される場合、`eop` の型は [`EopIau2000A`](@ref) でなければなりません。以下の表は、選択されたフレームに応じた EOP データの要件を示しています。

| モデル                  | ECI      | ECEF   | EOP データ      |
|:-------------------- |:-------- |:------ |:------------ |
| IAU-76/FK5           | `GCRF`   | `ITRF` | EOP IAU1980  |
| IAU-76/FK5           | `J2000`  | `ITRF` | EOP IAU1980  |
| IAU-76/FK5           | `MOD`    | `ITRF` | EOP IAU1980  |
| IAU-76/FK5           | `TOD`    | `ITRF` | EOP IAU1980  |
| IAU-76/FK5           | `TEME`   | `ITRF` | EOP IAU1980  |
| IAU-76/FK5           | `GCRF`   | `PEF`  | EOP IAU1980  |
| IAU-76/FK5           | `J2000`  | `PEF`  | 不要¹          |
| IAU-76/FK5           | `MOD`    | `PEF`  | 不要¹          |
| IAU-76/FK5           | `TOD`    | `PEF`  | 不要¹          |
| IAU-76/FK5           | `TEME`   | `PEF`  | 不要¹          |
| IAU-2006/2010 CIOベース | `CIRS`   | `ITRF` | EOP IAU2000A |
| IAU-2006/2010 CIOベース | `GCRF`   | `ITRF` | EOP IAU2000A |
| IAU-2006/2010 CIOベース | `CIRS`   | `TIRS` | 不要¹          |
| IAU-2006/2010 CIOベース | `GCRF`   | `TIRS` | 不要¹ ²        |
| IAU-2006/2010 春分点ベース | `ERS`    | `TIRS` | EOP IAU2000A |
| IAU-2006/2010 春分点ベース | `MOD06`  | `ITRF` | EOP IAU2000A |
| IAU-2006/2010 春分点ベース | `MJ2000` | `ITRF` | EOP IAU2000A |
| IAU-2006/2010 春分点ベース | `ERS`    | `TIRS` | 不要¹ ³        |
| IAU-2006/2010 春分点ベース | `MOD06`  | `TIRS` | 不要¹ ³        |
| IAU-2006/2010 春分点ベース | `MJ2000` | `TIRS` | 不要¹ ³        |

`¹`: この場合、UTC はグリニッジ平均恒星時を計算するために UT1 と等しいと仮定されます。これは近似ですが、一部のアプリケーションには十分に正確であるはずです。EOP データが提供されている場合、UT1 は正確に計算されます。

`²`: この場合、自由コア揺動と天体中間極（CIP）位置の時間依存効果を考慮する項は利用できず、精度が低下します。

`³`: この場合、自由コア揺動による傾斜と経度の揺動を修正する項は利用できず、精度が低下します。

!!! info
    この関数では、EOP 補正が提供されていない場合、MOD および TOD フレームは元の IAU-76/FK5 理論を考慮して計算されます。そうでない場合、修正されたフレームが使用されます。


## 例

```julia-repl
julia> eop_iau1980 = fetch_iers_eop(Val(:IAU1980));

julia> r_eci_to_ecef(DCM, GCRF(), ITRF(), date_to_jd(1986, 06, 19, 21, 35, 0), eop_iau1980)
DCM{Float64}:
 -0.619267    -0.78518     -0.000797312
  0.78518     -0.619267     0.00106478
 -0.00132979   3.33509e-5   0.999999

julia> r_eci_to_ecef(GCRF(), ITRF(), date_to_jd(1986, 06, 19, 21, 35, 0), eop_iau1980)
DCM{Float64}:
 -0.619267    -0.78518     -0.000797312
  0.78518     -0.619267     0.00106478
 -0.00132979   3.33509e-5   0.999999

julia> r_eci_to_ecef(J2000(), PEF(), date_to_jd(1986, 06, 19, 21, 35, 0))
DCM{Float64}:
 -0.619271    -0.785177    -0.000796885
  0.785176    -0.619272     0.00106622
 -0.00133066   3.45854e-5   0.999999

julia> r_eci_to_ecef(J2000(), PEF(), date_to_jd(1986, 06, 19, 21, 35, 0), eop_iau1980)
DCM{Float64}:
 -0.619267    -0.78518     -0.000796879
  0.78518     -0.619267     0.00106623
 -0.00133066   3.45854e-5   0.999999

julia> r_eci_to_ecef(Quaternion, GCRF(), ITRF(), date_to_jd(1986, 06, 19, 21, 35, 0), eop_iau1980)
Quaternion{Float64}:
  + 0.43631 + 0.000590997⋅i - 0.000305106⋅j - 0.899796⋅k

julia> eop_iau2000a = fetch_iers_eop(Val(:IAU2000A));

julia> r_eci_to_ecef(GCRF(), ITRF(), date_to_jd(1986, 06, 19, 21, 35, 0), eop_iau2000a)
DCM{Float64}:
 -0.619267    -0.78518     -0.000797311
  0.78518     -0.619267     0.00106478
 -0.00132979   3.33516e-5   0.999999

julia> r_eci_to_ecef(GCRF(), TIRS(), date_to_jd(1986, 06, 19, 21, 35, 0))
DCM{Float64}:
 -0.619271    -0.785177    -0.000796885
  0.785176    -0.619272     0.00106623
 -0.00133066   3.45884e-5   0.999999

julia> r_eci_to_ecef(Quaternion, GCRF(), ITRF(), date_to_jd(1986, 06, 19, 21, 35, 0), eop_iau2000a)
Quaternion{Float64}:
  + 0.43631 + 0.000590997⋅i - 0.000305106⋅j - 0.899796⋅k
```
