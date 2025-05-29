```
`ccf_1D!(ccf_out, ccf_covar_out, λs, fluxes, var; ccf_plan )`
```

スペクトルのクロスコリレーション関数をマスク付きで計算します。異なるマスク形状で動作する一般化されたバージョンです。進行中: ccfの共分散行列を計算するための一般化されたバージョンで、LSFを考慮するオプションがあります。

# 入力:

  * `ccf_out`: 出力を格納するためのサイズlength(calc*ccf*v_grid(plan))の1次元配列
  * `ccf_covar_out`: 出力を格納するためのサイズlength(calc*ccf*v_grid(plan))^2の2次元配列
  * `λs`: 波長の1次元配列
  * `fluxes`: フラックスの1次元配列
  * `var`: フラックス分散の1次元配列

# オプション引数:

  * `plan`: ccfを計算するためのパラメータ (BasicCCFPlan())
