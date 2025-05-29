```
py95(setting)
```

与えられた回帰設定に対してPena & Yohai (1995)アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。

# 説明

アルゴリズムは、与えられたモデルとデータに対する通常の最小二乗推定の結果を使用して影響行列を構築することから始まります。第二段階では、影響行列の固有構造を調べて、疑わしいデータのサブセットを検出します。

# 出力

  * `["outliers"]`: 外れ値のインデックスの配列
  * `["suspected.sets"]`: 影響行列の対応する固有値の観測値のインデックスの配列。
  * `["betas]`: クリーンな観測値を使用して推定された回帰係数のベクトル。

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(y ~ x1 + x2 + x3), hbk);
julia> py95(reg0001)
ict{Any,Any} with 2 entries:
  "outliers"       => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
  "suspected.sets" => Set([[14, 13], [43, 54, 24, 38, 22], [6, 10], [14, 7, 8, 3, 10, 2, 5, 6, 1, 9, 4…
```

# 参考文献

Peña, Daniel, and Victor J. Yohai. "The detection of influential subsets in linear  regression by using an influence matrix." Journal of the Royal Statistical Society:  Series B (Methodological) 57.1 (1995): 145-156.
