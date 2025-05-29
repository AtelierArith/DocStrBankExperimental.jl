```
minimizer(nd::Int; np::Int=35*ND, ne::Int=ND+1, ny::Int=0, method::String="global")
```

最小化のためのオブジェクトを作成/初期化するインターフェース関数。

## 引数:

  * `nd`:     最小化されるパラメータの次元。
  * `np`:     希望する個体数 (*オプション*)。
  * `ne`:     希望するエリートのサイズ (*オプション*)。
  * `ny`:     データ空間のサイズ（*変分推論*に必要）。
  * `method`: 希望するアルゴリズム ("global", "variational-inference")。
