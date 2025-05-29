```
mean_field_solution(problem::Problem, β::Vector{<:Real}, γ::Vector{<:Real})
```

### 入力

  * `problem::Problem`: 最適化問題を定義する `Problem` インスタンス。
  * `β::Vector{<:Real}`: QAOA ドライバーパラメータのベクトル。
  * `γ::Vector{<:Real}`: QAOA 問題パラメータのベクトル。

### 出力

  * 与えられた問題とスケジュールパラメータに対して計算された解のビット列。

### 注意事項

  * これは `mean_field_solution` の最初のディスパッチであり、与えられた問題とスケジュールパラメータに対して求められる解のビット列を計算します。
  * 解のビット列 $\boldsymbol{\sigma}_*$ は、最終スピンベクトルの $z$ 成分に基づいて次のように定義されます：

    $$
    \boldsymbol{\sigma}_* = \left(\mathrm{sign}(n_1^z), ..., \mathrm{sign}(n_N^z) \right).
    $$
