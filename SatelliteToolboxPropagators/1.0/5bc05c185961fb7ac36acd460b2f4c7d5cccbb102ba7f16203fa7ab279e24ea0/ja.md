```
fit_j2osc_mean_elements!(j2oscd::J2OsculatingPropagator{Tepoch, T}, vjd::AbstractVector{Tjd}, vr_i::AbstractVector{Tv}, vv_i::AbstractVector{Tv}; kwargs...) where {T<:Number, Tepoch<:Number, Tjd<:Number, Tv<:AbstractVector} -> KeplerianElements{Tepoch, T}, SMatrix{6, 6, T}
```

J2オスキュレーション軌道伝播器 `j2oscd` のための平均ケプラー要素のセットを、位置ベクトルのセット `vr_i` [m] と、配列 `vjd` [ユリウス日] の瞬間に慣性参照フレームで表された速度ベクトルのセット `vv_i` を使用してフィットします。

!!! note
    J2オスキュレーション軌道伝播器 `j2oscd` は、関数によって返されるケプラー要素で初期化されます。


# キーワード

  * `atol::Number`: 残差の絶対値に対する許容誤差。残差が任意の反復で `atol` より小さい場合、計算ループは停止します。   (**デフォルト** = 2e-4)
  * `rtol::Number`: 残差間の相対差に対する許容誤差。2つの連続した反復での残差間の相対差が `rtol` より小さい場合、計算ループは停止します。   (**デフォルト** = 2e-4)
  * `initial_guess::Union{Nothing, KeplerianElements}`: 平均要素フィッティングプロセスの初期推定。`nothing` の場合、アルゴリズムは `vr_i` と `vv_i` のオスキュレーション要素から初期推定を取得します。   (**デフォルト** = nothing)
  * `jacobian_perturbation::Number`: ヤコビアン行列を計算する際の有限差分を計算するための初期状態の摂動。   (**デフォルト** = 1e-3)
  * `jacobian_perturbation_tol::Number`: ヤコビアン行列を計算する際に摂動を受け入れるための許容誤差。計算された摂動が `jacobian_perturbation_tol` より小さい場合、絶対値が `jacobian_perturbation_tol` より大きくなるまで増加させます。   (**デフォルト** = 1e-7)
  * `max_iterations::Int`: 最小二乗フィッティングのために許可される最大反復回数。   (**デフォルト** = 50)
  * `mean_elements_epoch::Number`: フィットされた平均要素のエポック。   (**デフォルト** = vjd[end])
  * `verbose::Bool`: `true` の場合、アルゴリズムはデバッグ情報を `stdout` に出力します。   (**デフォルト** = true)
  * `weight_vector::AbstractVector`: 最小二乗アルゴリズムのための測定値の重みを持つベクトル。重み行列 `W` を、対角に `weight_vector` の要素を持つ対角行列として組み立てます。   (**デフォルト** = `@SVector(ones(Bool, 6))`)

# 戻り値

  * `KeplerianElements{Tepoch, T}`: フィットされたケプラー要素。
  * `SMatrix{6, 6, T}`: 最小二乗アルゴリズムの最終共分散行列。

# 例

```julia-repl
# ダミーのケプラー要素を使用して新しいJ2オスキュレーション軌道伝播器を割り当てます。
julia> j2oscd = j2osc_init(KeplerianElements{Float64, Float64}(0, 7000e3, 0, 0, 0, 0, 0));

julia> vr_i = [
           [-6792.402703741442, 2192.6458461287293, 0.18851758695295118] .* 1000,
           [-6357.88873265975, 2391.9476768911686, 2181.838771262736] .* 1000
       ];

julia> vv_i = [
           [0.3445760107690598, 1.0395135806993514, 7.393686131436984] .* 1000,
           [2.5285015912807003, 0.27812476784300005, 7.030323100703928] .* 1000
       ];

julia> vjd = [
           2.46002818657856e6,
           2.460028190050782e6
       ];

julia> orb, P = fit_j2osc_mean_elements!(j2oscd, vjd, vr_i, vv_i)
ACTION:   J2オスキュレーション伝播器のための平均要素をフィッティング中。
           反復        位置RMSE        速度RMSE           総RMSE       RMSE変動
                                     [km]             [km / s]                  [ ]
PROGRESS:          4          1.69161e-05           0.00260193              2.60198         -2.06772e-09 %

(KeplerianElements{Float64, Float64}: エポック = 2.46003e6 (2023-03-24T16:33:40.388), [0.9999427882949705 -0.0049011518111948425 … -0.00012021282848110985 -0.00011550570919063845; -0.00490115181520327 1.0007325785722665 … 0.0032661568999667063 3.8567115793316056e-5; … ; -0.00012021282849269182 0.003266156899966125 … 2.204826778451109e-5 5.382733068487529e-8; -0.00011550570919086411 3.8567115786674836e-5 … 5.382733066340212e-8 2.1657420198753813e-5])

julia> orb
KeplerianElements{Float64, Float64}:
           エポック :    2.46003e6 (2023-03-24T16:33:40.388)
 半長軸 : 7135.8        km
    離心率 :    0.00135383
     傾斜 :   98.4304     °
            RAAN :  162.113      °
  近点引数 :   64.9256     °
    真の異常 :  313.085      °
```
