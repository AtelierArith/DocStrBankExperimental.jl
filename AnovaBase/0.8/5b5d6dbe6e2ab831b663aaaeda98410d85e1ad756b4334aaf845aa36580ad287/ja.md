```
AnovaTable
```

ANOVAの係数と関連統計のテーブルです。主に`StatsBase.CoefTable`から修正されています。

# フィールド

  * `cols`: 各統計の値。
  * `colnms`: 統計の名前。
  * `rownms`: 各行の名前。
  * `pvalcol`: p値を表す列のインデックス。
  * `teststatcol`: テスト統計を表す列のインデックス。

# コンストラクタ

```
AnovaTable(cols::Vector, colnms::Vector, rownms::Vector, pvalcol::Int = 0, teststatcol::Int = 0)
AnovaTable(mat::Matrix, colnms::Vector, rownms::Vector, pvalcol::Int = 0, teststatcol::Int = 0)
```
