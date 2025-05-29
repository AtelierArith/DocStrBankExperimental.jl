```
freqtab(X; interval = 1.0, scale = minimum(X):interval:maximum(X))
```

`FreqTab`を作成します。これはEquateパッケージのSG設計方法に使用されます。

# 引数

  * `X` 欠損値を含まない生のテストスコアのベクトル。受験者の順序は、等化される別のベクトルに対応する必要があります。
  * `interval` スケールの間隔サイズ（Float64でなければなりません）。デフォルトは1.0です。ユーザーによって`scale`が指定された場合は無視されます。
  * `scale` テストスコアXのスケールを表すベクトルまたはStepRangeです。
