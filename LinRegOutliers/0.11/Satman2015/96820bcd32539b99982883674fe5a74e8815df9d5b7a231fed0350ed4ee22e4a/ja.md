```
satman2015(setting)
```

与えられた回帰設定に対してSatman (2015)アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。

# 説明

アルゴリズムは、非支配ソートアルゴリズムを使用して設計行列をソートすることから始まります。次に、前の段階で得られたランクを使用して初期の基本サブセットが構築されます。多くのCステップの後、高い標準化残差を持つ観測値が外れ値として報告されます。

# 出力

  * `["outliers]`": 外れ値のインデックスの配列。
  * `[betas]`: 回帰係数の配列。
  * `[residuals]`: 残差の配列。
  * `[standardized_residuals]`: 標準化残差の配列。

# 例

```julia-repl
julia> eg0001 = createRegressionSetting(@formula(y ~ x1 + x2 + x3), hbk);
julia> satman2015(reg0001)
Dict{Any,Any} with 1 entry:
  "outliers" => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 14, 47]

```

# 参考文献

Satman, Mehmet Hakan. "Fast online detection of outliers using least-trimmed squares  regression with non-dominated sorting based initial subsets."  International Journal of Advanced Statistics and Probability 3.1 (2015): 53.
