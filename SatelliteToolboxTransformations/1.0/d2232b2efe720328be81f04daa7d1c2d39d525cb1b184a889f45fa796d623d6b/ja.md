```
sv_ecef_to_ecef(sv::OrbitStateVector, ECEFo, ECEFf[, jd_utc::Number], eop) -> OrbitStateVector
```

地球中心、地球固定（ECEF）参照フレーム `ECEFo` から別の ECEF 参照フレーム `ECEFf` へ、軌道状態ベクトル `sv` をジュリアンデイ `jd_utc` [UTC] で変換します。もしエポック `jd_utc` が提供されていない場合、アルゴリズムは軌道状態ベクトル `sv` のエポック（`sv.t`）を使用します。アルゴリズムは地球の姿勢パラメータ（EOP） `eop` も必要とします。

!!! note
    より詳しい情報、特に起点と目的の参照フレームを指定する方法については、**拡張ヘルプ**を参照してください。


# 戻り値

  * `OrbitStateVector`: `ECEFf` 参照フレームに変換された軌道状態ベクトル `sv`。

# 拡張ヘルプ

## 変換モデル

回転を計算するために使用されるモデルは、起点と目的のフレームの選択に基づいて自動的に推測されます。**IAU-76/FK5 と IAU-2006/2010 フレームを混合することはサポートされていません。**

## サポートされている ECEF 参照フレーム

起点 `ECEFo` と目的 `ECEFf` の両方に対してサポートされている ECEF フレームは次のとおりです。

  * `ITRF()`: ECEF は国際地球参照フレーム（ITRF）として選択されます。
  * `PEF()`: ECEF は擬似地球固定（PEF）参照フレーム（IAU-76/FK5）として選択されます。
  * `TIRS()`: ECEF は地球中間参照システム（TIRS）（IAU-2006/2010）として選択されます。

## 地球の姿勢パラメータ（EOP）

サポートされている ECEF フレーム間の変換は **常に** EOP に依存します（[`fetch_iers_eop`](@ref) および [`read_iers_eop`](@ref) を参照）。IAU-76/FK5 モデルが使用される場合、`eop` の型は [`EopIau1980`](@ref) でなければなりません。そうでない場合、IAU-2006/2010 モデルが使用される場合、`eop` の型は [`EopIau2000A`](@ref) でなければなりません。

## 例

```julia-repl
julia> eop_iau1980 = fetch_iers_eop();

julia> jd_utc = date_to_jd(2004, 4, 6, 7, 51, 28.386009)
2.453101827411875e6

julia> r_itrf  = [-1033.4793830; 7901.2952754; 6380.3565958] * 1000;

julia> v_itrf  = [-3.225636520; -2.872451450; +5.531924446] * 1000;

julia> sv_itrf = OrbitStateVector(jd_utc, r_itrf, v_itrf);

julia> sv_ecef_to_ecef(sv_itrf, ITRF(), PEF(), eop_iau1980)
OrbitStateVector{Float64, Float64}:
  epoch : 2.4531e6 (2004-04-06T07:51:28.386)
      r : [-1033.48, 7901.31, 6380.34]   km
      v : [-3.22563, -2.87244, 5.53193]  km/s
```
