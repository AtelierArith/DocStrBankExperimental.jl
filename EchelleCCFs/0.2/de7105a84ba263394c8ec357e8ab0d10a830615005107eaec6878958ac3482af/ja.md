```
`ccf_1D!(ccf_out, λs, fluxes; ccf_plan )`
```

スペクトルのクロスコリレーション関数をマスクと共に計算します。異なるマスク形状で動作する一般化されたバージョンです。

# 入力:

  * `ccf_out`: 出力を格納するためのサイズ length(calc*ccf*v_grid(plan)) の 1 次元配列
  * `λs`: 波長の 1 次元配列
  * `fluxes`: フラックスの 1 次元配列

# オプション引数:

  * `plan`: ccf を計算するためのパラメータ (BasicCCFPlan())
