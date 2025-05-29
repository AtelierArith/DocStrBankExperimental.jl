```
get_states(simulation::DiscretizedSPAC; days_to_read_out_d = nothing)
```

入力と状態変数の量（および同位体組成）を含むDataFrameを返します：PREC、GWAT、INTS、INTR、SNOW、（量のみ：CC、SNOWLQ）、（署名のみ：XYLEM）。RWUフラックスは`get_fluxes()`を使用して取得できます。デフォルトでは、値は各シミュレーション日ごとに返されます。ユーザーは、入力引数`days_to_read_out_d`を使用してタイムステップをオプションで定義できます：

  * `:integrator_step`を指定すると、各シミュレーションタイムステップごとに取得できます
  * 数値ベクトル、例えば`days_to_read_out_d = 1:1.0:100`を指定すると、`simulation.parametrizedSPAC.reference_date`からの特定の日を取得できます

スカラー状態変数や土壌状態のサブセットは、次のようにして作成できます：

```
simout_states = get_states(simulation)
simout_states[:, Not(r"[0-9]mm$")]    # 深さ情報を含む列を除外してスカラー状態のみを選択
simout_states[:, r"(dates)|([0-9]mm)"] # 深さ情報を含む列を選択してベクトル状態のみを選択
```

返される内容：

```
366×108 DataFrame
 Row │ dates                GWAT_mm  INTS_mm   INTR_mm       SNOW_mm  CC_MJm2     SNOWLQ_mm  SWAT_mm  GWAT_d18O  INTS_d18O  INTR_d18O  SNOW_d18O  XYLEM_d18O  ⋯ δ18O_permil_50mm  δ18O_permil_100mm  δ18O_permil_1 ⋯ ψ_kPa_1100mm
     │ DateTime             Float64  Float64   Float64       Float64  Float64     Float64    Float64  Float64    Float64    Float64    Float64    Float64     ⋯ Float64           Float64            Float64       ⋯ Float 64
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 2021-01-01T00:00:00      1.0  0.0        0.0           0.0     0.0          0.0       90.2641  -13.0        -13.0      -13.0      -13.0     -10.1111  ⋯         -10.1111           -10.1111           -10. ⋯ -7
   2 │ 2021-01-02T00:00:00      1.0  0.0        0.0           0.0     0.0          0.0       90.4532  -12.5973     -15.04     -15.04     -15.04    -10.1111            -10.1111           -10.1111           -10. ⋯ -6.43
```
