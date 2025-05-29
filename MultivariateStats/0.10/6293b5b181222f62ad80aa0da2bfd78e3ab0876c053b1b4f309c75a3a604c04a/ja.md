```
fit(LinearDiscriminant, Xp, Xn; covestimator = SimpleCovariance())
```

正のサンプルと負のサンプルの両方を考慮してLDAを実行します。この関数は以下のパラメータを受け入れます：

**パラメータ**

  * `Xp`: 正のクラスのサンプル行列。
  * `Xn`: 負のクラスのサンプル行列。

**キーワード引数:**

  * `covestimator`: クラス間共分散のためのカスタム共分散推定器。共分散行列は `cov(covestimator_between, #=data=#; dims=2, mean=zeros(#=...=#)` として計算されます。他のパッケージで利用可能なカスタム共分散推定器は、観測数よりも特徴数が多いデータに対してより堅牢な判別をもたらす可能性があります。
