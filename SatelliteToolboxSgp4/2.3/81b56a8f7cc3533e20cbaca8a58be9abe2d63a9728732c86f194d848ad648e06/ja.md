```
fit_sgp4_tle(vjd::AbstractVector{Tjd}, vr_teme::AbstractVector{Tv}, vv_teme::AbstractVector{Tv}; kwargs...) where {T<:Number, Tepoch<:Number, Tjd<:Number, Tv<:AbstractVector} -> TLE, SMatrix{7, 7, T}
```

SGP4軌道伝播器のための二行要素セット（`TLE`）を、位置ベクトルのセット`vr_teme` [km]と速度ベクトルのセット`vv_teme` [km / s]で表される振動要素を使用してフィットします。これらは、配列`vjd` [ユリウス日]の瞬間における真赤道、平均春分点基準フレーム（TEME）で表されています。

このアルゴリズムは**[1]**に基づいています。

!!! note
    このアルゴリズムのバージョンは、デフォルト定数`sgp4c_wgs84`を使用して新しいSGP4伝播器を割り当てます。別の定数セットが必要な場合は、代わりに関数[`fit_sgp4_tle!`](@ref)を使用してください。


# キーワード

  * `atol::Number`: 残差の絶対値に対する許容誤差。残差が任意の反復で`atol`よりも低い場合、計算ループは停止します。   (**デフォルト** = 2e-4)
  * `rtol::Number`: 残差間の相対差に対する許容誤差。2つの連続した反復での残差間の相対差が`rtol`よりも低い場合、計算ループは停止します。   (**デフォルト** = 2e-4)
  * `estimate_bstar::Bool`: `true`の場合、アルゴリズムはB*パラメータを推定しようとします。そうでない場合は、0または初期推定値の値に設定されます（**初期推定**のセクションを参照）。   (**デフォルト** = true)
  * `initial_guess::Union{Nothing, AbstractVector, TLE}`: TLEフィッティングプロセスの初期推定。`nothing`の場合、アルゴリズムは`vr_teme`と`vv_teme`の振動要素から初期推定を取得します。詳細については、**初期推定**のセクションを参照してください。   (**デフォルト** = nothing)
  * `jacobian_perturbation::Number`: ヤコビアン行列を計算する際の有限差分を計算するための初期状態の摂動。   (**デフォルト** = 1e-3)
  * `jacobian_perturbation_tol::Number`: ヤコビアン行列を計算する際に摂動を受け入れるための許容誤差。計算された摂動が`jacobian_perturbation_tol`よりも低い場合、絶対値が`jacobian_perturbation_tol`よりも高くなるまで増加させます。   (**デフォルト** = 1e-7)
  * `max_iterations::Int`: 最小二乗フィッティングのために許可される最大反復回数。   (**デフォルト** = 50)
  * `mean_elements_epoch::Number`: フィットされたTLEのエポック。   (**デフォルト** = vjd[end])
  * `verbose::Bool`: `true`の場合、アルゴリズムはデバッグ情報を`stdout`に出力します。   (**デフォルト** = true)
  * `weight_vector::AbstractVector`: 最小二乗アルゴリズムの測定重みを持つベクトル。重み行列`W`を、対角に`weight_vector`の要素を持つ対角行列として組み立てます。   (**デフォルト** = `@SVector(ones(Bool, 6))`)
  * `classification::Char`: 出力TLEのための衛星分類文字。   (**デフォルト** = 'U')
  * `element_set_number::Int`: 出力TLEのための要素セット番号。   (**デフォルト** = 0)
  * `international_designator::String`: 出力TLEのための国際設計者文字列。   (**デフォルト** = "999999")
  * `name::String`: 出力TLEのための衛星名。   (**デフォルト** = "UNDEFINED")
  * `revolution_number::Int`: 出力TLEのための周回数。   (**デフォルト** = 0)
  * `satellite_number::Int`: 出力TLEのための衛星番号。   (**デフォルト** = 9999)

# 戻り値

  * `TLE`: フィットされたTLE。
  * `SMatrix{7, 7, T}`: 最小二乗アルゴリズムの最終共分散行列。

# 初期推定

このアルゴリズムは、振動状態ベクトルのセットに基づいてTLEをフィットさせるために最小二乗アルゴリズムを使用します。システムはカオス的であるため、良好な初期推定はアルゴリズムの収束にとって重要です。キーワード`initial_guess`を使用して初期推定を提供できます。

`initial_guess`が`TLE`の場合、関数[`update_sgp4_tle_epoch!`](@ref)を使用してTLEエポックを`mean_elements_epoch`の希望のものに更新します。その後、この新しいTLEを初期推定として使用します。

`initial_guess`が`AbstractVector`の場合、このベクトルをアルゴリズムの初期平均状態ベクトルとして使用します。次の7つの要素を含む必要があります：

```
┌                                    ┐
│ IDs 1 to 3: 平均位置 [km]         │
│ IDs 4 to 6: 平均速度 [km / s]     │
│ ID  7:      Bstar         [1 / er] │
└                                    ┘
```

`initial_guess`が`nothing`の場合、アルゴリズムは`mean_elements_epoch`に最も近い振動状態ベクトルを取得し、それを初期平均状態ベクトルとして使用します。この場合、エポックは`vjd`の振動データの同じエポックに設定されます。フィットされたTLEが取得されると、アルゴリズムは関数[`update_sgp4_tle_epoch!`](@ref)を使用してそのエポックを`mean_elements_epoch`に変更します。

!!! note
    `initial_guess`が`nothing`でない場合、B*の初期推定はTLEまたは状態ベクトルから取得されます。したがって、`estimate_bstar`が`false`の場合、この初期値は一定に保たれます。


# 例

```julia-repl
julia> vr_teme = [
           [-6792.402703741442, 2192.6458461287293, 0.18851758695295118],
           [-6357.88873265975, 2391.9476768911686, 2181.838771262736]
       ];

julia> vv_teme = [
           [0.3445760107690598, 1.0395135806993514, 7.393686131436984],
           [2.5285015912807003, 0.27812476784300005, 7.030323100703928]
       ];

julia> vjd = [
           2.46002818657856e6,
           2.460028190050782e6
       ];

julia> tle, P = fit_sgp4_tle(vjd, vr_teme, vv_teme; estimate_bstar = false)
ACTION:   TLEをフィッティング中。
           反復        位置RMSE        速度RMSE           総RMSE       RMSE変動
                                     [km]             [km / s]                  [ ]
PROGRESS:          3          5.80079e-09          4.38304e-07          4.38343e-07             -99.9514 %

(TLE: UNDEFINED (Epoch = 2023-03-24T16:33:40.388), [1.085542785763592 -0.02468955108588304 … -0.07505082051267041 -5691.217934788844; -0.024689551096344593 1.0180284581267773 … 0.023015858293558573 1745.6307022638805; … ; -0.07505082051315085 0.023015858293655808 … 0.06515845129137222 4946.150014964575; -5691.217934826224 1745.630702271188 … 4946.15001496459 3.7558624425042915e8])

julia> tle
TLE:
                      Name : UNDEFINED
          Satellite number : 9999
  International designator : 999999
        Epoch (Year / Day) : 23 /  83.69005079 (2023-03-24T16:33:40.388)
        Element set number : 0
              Eccentricity :   0.00012463
               Inclination :  98.43040000 deg
                      RAAN : 162.11312239 deg
       Argument of perigee : 136.15040637 deg
              Mean anomaly : 241.97934028 deg
           Mean motion (n) :  14.40814157 revs / day
         Revolution number : 0
                        B* :            0 1 / er
                     ṅ / 2 :            0 rev / day²
                     n̈ / 6 :            0 rev / day³
```

# 参考文献

  * **[1]** Vallado, D. A., Crawford, P (2008). SGP4軌道決定. アメリカ航空宇宙学会。
