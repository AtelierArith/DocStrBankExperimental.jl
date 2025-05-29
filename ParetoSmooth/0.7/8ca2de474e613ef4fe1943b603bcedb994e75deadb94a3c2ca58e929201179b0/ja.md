```
function loo_compare(
    cv_results...;
    sort_models::Bool=true,
    best_to_worst::Bool=true,
    [, model_names::Tuple{Symbol}]
) -> ModelComparison
```

複数の [`PsisLoo`](@ref) オブジェクトからモデル比較テーブルを構築します。

# 引数

  * `cv_results`: 比較する1つ以上の [`PsisLoo`](@ref) オブジェクト。代わりに、`PsisLoo` オブジェクトのタプルまたは名前付きタプルを渡すこともできます。名前付きタプルが渡された場合、これらの名前が各モデルのラベルとして使用されます。
  * `model_names`: モデルを識別するために使用される文字列またはシンボルのベクターまたはタプル。指定がない場合、モデルは引数の順序に従って番号付けされます。
  * `sort_models`: 合計スコアでモデルをソートします。
  * `high_to_low`: モデルを最高から最低のスコアでソートします。`false` の場合、順序が逆になります。

関連情報: [`ModelComparison`](@ref), [`PsisLoo`](@ref), [`psis_loo`](@ref)
