```
SmoothLP(names, order::Int=3, ndiff::Int=3; kwargs)
```

[`SmoothLP`](@ref)のコンストラクタ。

# 引数

  * `names`: ペナルライズスプラインでフィットするデータテーブルの変数の列インデックス。
  * `order`: スプライン基底における多項式項の最高次数。
  * `ndiff`: Bスプライン係数をペナルティするために使用される有限差分演算子の次数。

# キーワード

  * `search::ModelSelection=grid()`: 代替スムージングパラメータを生成するための方法。
  * `criterion::SearchCriterion=LOOCV()`: 最適なパラメータを選択するための基準。
  * `fullX::Bool=false`: スムージングに関与しない回帰行列が保持されるかどうか。
