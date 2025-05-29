```
function sequentialcovering(
    X::AbstractLogiset,
    y::AbstractVector{<:CLabel},
    w::Union{Nothing,AbstractVector{U},Symbol} = default_weights(length(y));
    kwargs...
)::DecisionList where {U<:Real}
```

ログアイセット `X` とラベル `y`、および重み `w` に基づいて決定リストを学習します。これは古典的な [sequential covering](https://christophm.github.io/interpretable-ml-book/rules.html#sequential-covering) 学習スキームに従い、単一のルールを反復的に学習し、新たにカバーされたインスタンスを削除することを含みます。

# キーワード引数

  * `searchmethod::SearchMethod`: 単一のルールを見つけるための検索方法（[`SearchMethod`](@ref)を参照）;
  * `max_rulebase_length::Union{Nothing,Integer}` はルールベースの最大長;
  * `suppress_parity_warning::Bool` が `true` の場合、パリティ警告を抑制します。
  * `unorderedstrategy::Bool`: TODO @Edo 説明
  * `min_rule_coverage::Integer`:
  * 追加のキーワード引数は `searchmethod` にインプットされ、その元の値を置き換えます。

# 例

```julia-repl

julia> X = PropositionalLogiset(iris_dataframe);

julia> y = Vector{CLabel}(iris_labels);

julia> sequentialcovering(X, y)
▣
├[1/22]┐(:sepal_length ≤ 4.8)
│└ setosa
├[2/22]┐(:sepal_length ≥ 7.1)
│└ virginica
├[3/22]┐(:sepal_length ≥ 7.0)
│└ versicolor
├[4/22]┐(:sepal_width ≤ 2.0)
│└ versicolor
├[5/22]┐(:sepal_width ≥ 3.5)
│└ setosa
├[6/22]┐(:petal_length ≤ 1.7)
│└ setosa
├[7/22]┐(:petal_length ≤ 4.4)
│└ versicolor
├[8/22]┐(:sepal_length ≤ 4.9)
│└ virginica
├[9/22]┐(:sepal_length ≤ 5.4)
│└ versicolor
├[10/22]┐(:petal_length ≤ 4.7)
│└ versicolor
├[11/22]┐(:sepal_length ≤ 5.8)
│└ virginica
├[12/22]┐(:sepal_width ≤ 2.2)
│└ virginica
├[13/22]┐(:sepal_width ≥ 3.3)
│└ virginica
├[14/22]┐(:petal_length ≥ 5.2)
│└ virginica
├[15/22]┐(:petal_width ≤ 1.4)
│└ versicolor
├[16/22]┐(:petal_width ≥ 1.9)
│└ virginica
├[17/22]┐(:sepal_length ≥ 6.7)
│└ versicolor
├[18/22]┐(:sepal_width ≤ 2.5)
│└ versicolor
├[19/22]┐(:sepal_length ≥ 6.1)
│└ virginica
├[20/22]┐(:sepal_width ≤ 2.7)
│└ versicolor
├[21/22]┐(:sepal_length ≥ 6.0)
│└ virginica
├[22/22]┐(:sepal_width ≤ 3.0)
│└ virginica
└✘ versicolor
```

さらに [`SearchMethod`](@ref)、[`BeamSearch`](@ref)、[`PropositionalLogiset`](@ref)、[`DecisionList`](@ref) を参照してください。
