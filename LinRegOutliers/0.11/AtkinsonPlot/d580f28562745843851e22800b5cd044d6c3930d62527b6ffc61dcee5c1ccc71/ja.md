```
    atkinsonstalactiteplot(setting, iters, crit)
```

atkinson94アルゴリズムを実行し、さらに論文で説明されているようにStalactiteテキストプロットを描画します。現在のところ、100ポイント未満のデータに対して機能します（標準の画面幅は80-120です）。詳細については`atkinson94`を参照してください。

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。
  * `iters::Int`: ランダムサンプルの数。
  * `crit::Float64`: 残差のための臨界値

# 参考文献

Atkinson, Anthony C. "Fast very robust methods for the detection of multiple outliers." Journal of the American Statistical Association 89.428 (1994): 1329-1339.
