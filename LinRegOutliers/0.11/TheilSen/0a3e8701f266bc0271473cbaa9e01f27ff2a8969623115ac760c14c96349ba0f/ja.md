```
theilsen(setting, m, nsamples = 5000)
```

Theil-Sen推定量による重回帰分析。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。
  * `m::Int`: 各イテレーションで使用される観測値の数。この数は[p, n]の範囲内でなければならず、pは回帰変数の数、nは観測値の数です。
  * `nsamples::Int`: mサンプルの数。デフォルトは5000。

# 説明

この関数は回帰フォーミュラとデータセットから始まります。各イテレーションで使用される観測値の数はユーザーによって指定されます。関数はデータセットからランダムにm個の観測値を選択し、通常の最小二乗推定を行います。推定された係数は保存されます。このプロセスは、nsamples回の回帰が推定されるまで繰り返されます。次に、推定された係数の多変量中央値が計算されます。この場合、多変量中央値はすべての推定された係数への距離の合計を最小化する点です。最適化問題にはHooke & Jeevesアルゴリズムが使用されます。

# 参考文献

Dang, X., Peng, H., Wang, X., & Zhang, H. (2008). Theil-sen estimators in a multiple linear regression model. Olemiss Edu.
