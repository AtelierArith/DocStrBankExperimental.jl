```
update_sgp4_tle_epoch(tle::TLE, new_epoch::Union{Number, DateTime}; kwargs...) -> TLE
```

`tle` のエポックを SGP4 平均要素で `new_epoch` に更新します。`new_epoch` はユリウス日または `DateTime` で表すことができます。

!!! notes
    このアルゴリズムバージョンは、デフォルト定数 `sgp4c_wgs84` を使用して新しい SGP4 推進器を割り当てます。別の定数セットが必要な場合は、代わりに関数 [`update_sgp4_tle_epoch!`](@ref) を使用してください。


この関数は、TLE エポックを更新するために次のアルゴリズムを使用します：

1. `tle` で SGP4 推進器を初期化します；
2. 軌道を `new_epoch` まで伝播させ、TEME 参照フレームでの振動状態ベクトルを取得します；および
3. 新しいエポックを考慮しながら、同じ振動状態ベクトルを提供する新しい TLE をフィットさせます。

3 番目のステップでは、関数 [`fit_sgp4_tle!`](@ref) を使用します。したがって、いくつかのキーワードはそれに関連しています。詳細については、[`fit_sgp4_tle!`](@ref) のドキュメントを参照してください。

# キーワード

  * `atol::Number`: 残差の絶対値に対する許容誤差。任意の反復で残差が `atol` より小さい場合、計算ループは停止します。 (**デフォルト** = 2e-4)
  * `rtol::Number`: 残差間の相対差に対する許容誤差。任意の反復で、2 回の連続した反復における残差間の相対差が `rtol` より小さい場合、計算ループは停止します。 (**デフォルト** = 2e-4)
  * `max_iterations::Int`: 最小二乗フィッティングに許可される最大反復回数。 (**デフォルト** = 50)
  * `verbose::Bool`: `true` の場合、アルゴリズムはデバッグ情報を `stdout` に出力します。 (**デフォルト** = true)

# 例

```julia-repl
julia> tle = tle"""
          AMAZONIA 1
          1 47699U 21015A   23083.68657856  .00000000  00000-8  43000-3 0  9999
          2 47699  98.4304 162.1097 0001247 136.2017 223.9283 14.40814394108652
          """
TLE:
                      Name : AMAZONIA 1
          Satellite number : 47699
  International designator : 21015A
        Epoch (Year / Day) : 23 /  83.68657856 (2023-03-24T16:28:40.388)
        Element set number : 999
              Eccentricity :   0.00012470
               Inclination :  98.43040000 deg
                      RAAN : 162.10970000 deg
       Argument of perigee : 136.20170000 deg
              Mean anomaly : 223.92830000 deg
           Mean motion (n) :  14.40814394 revs / day
         Revolution number : 10865
                        B* :      0.00043 1 / er
                     ṅ / 2 :            0 rev / day²
                     n̈ / 6 :            0 rev / day³

julia> update_sgp4_tle_epoch(tle, DateTime("2023-06-19"))
ACTION:   Fitting the TLE.
           Iteration        Position RMSE        Velocity RMSE           Total RMSE       RMSE Variation
                                     [km]             [km / s]                  [ ]
PROGRESS:          4          2.79523e-06          2.57681e-09          2.79523e-06             -99.9999 %

TLE:
                      Name : AMAZONIA 1
          Satellite number : 47699
  International designator : 21015A
        Epoch (Year / Day) : 23 / 170.00000000 (2023-06-19T00:00:00)
        Element set number : 999
              Eccentricity :   0.00012727
               Inclination :  98.43040000 deg
                      RAAN : 247.20081879 deg
       Argument of perigee : 237.78423781 deg
              Mean anomaly : 121.83893462 deg
           Mean motion (n) :  14.41052177 revs / day
         Revolution number : 10865
                        B* :      0.00043 1 / er
                     ṅ / 2 :            0 rev / day²
                     n̈ / 6 :            0 rev / day³
```
