```
SPAC
```

土壌-植物-大気連続体モデルのインスタンスで、以下のフィールドを持ちます：

  * `reference_date`: 内部での数値日を実際の日付に関連付けるためのDateTime
  * `tspan`: タプル `(0, Int)` 参照日からの日数での利用可能な入力データの時間範囲
  * `solver_options`: `NamedTuple`: (compute*intermediate*quantities, simulate_isotopes, DTIMAX, DSWMAX, DPSIMAX)、モデルのためのいくつかのソルバーオプションを含む
  * `soil_discretization`: `DataFrame` で `soil_discretizations.csv` からの内容を持ち、すなわち以下の列を含む： `Upper_m`,`Lower_m`,`Rootden_`,`uAux_PSIM_init_kPa`,`u_delta18O_init_permil`,`u_delta2H_init_permil`

    ```
      `soil_discretizations.csv` から読み込まれるか、または loadSPAC() に引数として指定されます。
      未使用の値は NaN です。
    ```
  * `forcing`: `NamedTuple`: (:meteo, :meteo*iso, :storm*durations)、大気強制を含む

      * `forcing.meteo`: 日次の大気変数を含むDataFrame
      * `forcing.meteo_iso`: 降水の同位体署名を含むDataFrame
      * `forcing.storm_durations`: 各月の典型的な嵐の持続時間を時間単位で示すDataFrame
  * `pars`: `NamedTuple`: (:params, )

      * `pars.params`: `NamedTuple`: ()、モデルのスカラーパラメータ値を含む
      * `pars.root_distribution`: いずれか：

          * `NamedTuple`: (beta, theta, z*rootMax*m = nothing) 深さに対する根の分布のパラメータ化 (f(z*m) は z*m がメートルで負の下向き)。
          * `NamedTuple`: (alpha = 0.97, z*rootMax*m = nothing) 深さに対する根の分布のパラメータ化 (f(z*m) は z*m がメートルで負の下向き)。
          * または文字列: `"soil_discretization.csv"` これは `soil_discretizations.csv` で定義される必要があることを意味します。
      * `pars.IC_scalar`: `NamedTuple`: ()、スカラー状態変数の初期条件を含む
      * `pars.IC_soil`: 状態変数の初期条件（スカラーまたは土壌に関連）。いずれか：

          * `NamedTuple`: (PSIM*init, δ18O*init, δ2H_init)、初期条件の定数値を含む
          * [未実装:] `NamedTuple`: (PSIM*init, δ18O*init, δ2H_init)、引数 Δz を持つ初期値の関数を含む
          * または文字列: `"soil_discretization.csv"` これは `soil_discretizations.csv` で定義される必要があることを意味します。
      * `pars.canopy_evolution`: キャノピーのパラメータ (LAI, SAI, DENSEF, HEIGHT) をパーセントで相対的に示す。いずれか：

          * `NamedTuple`: (DENSEF*rel = 100, HEIGHT*rel = 100, SAI*rel = 100, LAI*rel = (DOY*Bstart, Bduration, DOY*Cstart, Cduration, LAI*perc*BtoC, LAI*perc*CtoB))、定数値と LAI_relative 補間のためのパラメータを含む
          * またはDataFrame: 日次の値を持つ
      * `pars.soil_horizons`: 土壌層/地平線の説明と土壌水理パラメータを含むDataFrame
