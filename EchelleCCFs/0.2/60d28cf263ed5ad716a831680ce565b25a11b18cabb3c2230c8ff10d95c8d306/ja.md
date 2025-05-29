```
`ccf_1D( λs, fluxes; ccf_plan )`
スペクトルのクロスコリレーション関数をマスク付きで計算します。
```

# 入力:

  * `λs`: 波長の1次元配列
  * `fluxes`: フラックスの2次元配列、最初の次元に沿った個々のスペクトル

# オプション引数:

  * `ccf_plan`: ccfを計算するためのパラメータ (BasicCCFPlan())

# 戻り値:

  * サイズが (length(calc*ccf*v_grid(plan)), size(flux, 2)) の2次元配列
