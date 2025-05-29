```
pca(data::PopData; maxpc::Int = 0, method::Symbol = :svd, missings::String = "mean", pratio::Float64 = 0.99, center::Bool = false, scale::Bool = true)
```

PopDataオブジェクトに対して主成分分析を実行します。インデックス可能な`MultivariateStats.PCA`オブジェクトを返します。

#### 引数

  * `data::PopData`: `PopData`オブジェクト

#### キーワード引数

  * `method::Symbol`: 使用するPCAメソッド（デフォルト: `:svd`）

      * `:cov`: 共分散行列の分解に基づく
      * `:svd`: 入力データの特異値分解に基づく
  * `maxpc::Int`: 保持する主成分の最大数（デフォルト: 0 = `(min(d, ncol-1))`）
  * `missings::String`: アレル頻度行列における欠損遺伝子型の扱い方（デフォルト: `mean`）

      * `"mean"`: `missing`値をそのローカスにおけるアレルの平均頻度で置き換える
      * `"missing"`: `missing`値をそのまま保持する
      * `"zero"`: `missing`値を`0`で置き換える
  * `pratio::Float64`: 主サブスペースに保存される分散の最大比（デフォルト = `0.99`）
  * `center::Bool`: アレル頻度行列を中心化するかどうか（デフォルト: `false`）
  * `scale::Bool`: アレル頻度行列をZスコアスケールするかどうか（デフォルト: `true`）
