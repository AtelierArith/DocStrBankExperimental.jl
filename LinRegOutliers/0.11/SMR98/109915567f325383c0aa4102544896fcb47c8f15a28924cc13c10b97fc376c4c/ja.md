```
smr98(setting)
```

与えられた回帰設定に対して、Sebert、Monthomery、Rollier（1998）アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: 数式とデータセットを持つRegressionSettingオブジェクト。

# 説明

このアルゴリズムは、与えられたモデルとデータに対して通常の最小二乗推定から始まります。残差とフィッティングされた応答は、推定されたモデルを使用して計算されます。標準化された残差と標準化されたフィッティングされた応答を使用して階層的クラスタリング分析が適用されます。著者によって提案されたように、しきい値（例：Majona基準）を使用してクラスタの木構造が切り取られます。比較的少数の観測値を持つサブツリーが外れ値のクラスタとして宣言されることが期待されます。

# 出力

  * `["outliers"]`: 外れ値のインデックスの配列。
  * `["betas"]`: 回帰係数のベクトル。

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> smr98(reg0001)
Dict{String, Vector} with 2 entries:
  "betas"    => [-55.4519, 1.15692]
  "outliers" => [15, 16, 17, 18, 19, 20, 21, 22, 23, 24]
```

# 参考文献

Sebert, David M., Douglas C. Montgomery, and Dwayne A. Rollier. "A clustering algorithm for  identifying multiple outliers in linear regression." Computational statistics & data analysis  27.4 (1998): 461-484.
