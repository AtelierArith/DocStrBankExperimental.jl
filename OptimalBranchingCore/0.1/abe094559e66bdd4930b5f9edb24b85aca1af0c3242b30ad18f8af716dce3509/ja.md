```
branch_and_reduce(problem::AbstractProblem, config::BranchingStrategy; reducer::AbstractReducer=NoReducer(), result_type=Int, show_progress=false)
```

指定されたソルバー構成を使用して、与えられた問題を分岐させます。

### 引数

  * `problem`: 解決すべき問題インスタンス。
  * `config`: ソルバーの構成で、[`BranchingStrategy`](@ref) インスタンスです。

### キーワード引数

  * `reducer::AbstractReducer=NoReducer()`: 問題のサイズを縮小するためのリデューサー。
  * `result_type::Type{TR}`: ソルバーが生成する結果の型。

### 戻り値

`result_type` に応じて異なる型を持つ可能性がある結果の値。
