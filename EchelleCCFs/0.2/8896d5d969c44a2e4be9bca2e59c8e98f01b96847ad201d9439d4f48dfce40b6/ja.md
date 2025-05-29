```
`ccf_1D!(ccf_out, ccf_var_out, λs, fluxes, var; ccf_plan )`
```

スペクトルのマスクとのクロス相関関数を計算します。異なるマスク形状で動作する一般化されたバージョンです。

# 入力:

  * `ccf_out`: 出力を格納するためのサイズ length(calc*ccf*v_grid(plan)) の 1-d 配列
  * `ccf_var_out`: 出力を格納するためのサイズ length(calc*ccf*v_grid(plan)) の 1-d 配列
  * `λs`: 波長の 1-d 配列
  * `fluxes`: フラックスの 1-d 配列
  * `var`: フラックス分散の 1-d 配列

# オプション引数:

  * `plan`: ccf を計算するためのパラメータ (BasicCCFPlan())
