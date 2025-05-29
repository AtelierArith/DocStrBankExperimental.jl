```
`ccf_1D( λs, fluxes; ccf_plan )`
スペクトルのクロスコリレーション関数をマスクと共に計算します。
```

# 入力:

  * `λs`: 波長の1次元配列
  * `fluxes`: フラックスの1次元配列

# オプション引数:

  * `ccf_plan`: ccfを計算するためのパラメータ (BasicCCFPlan())

# 戻り値:

  * サイズが length(calc*ccf*v_grid(plan)) の1次元配列
