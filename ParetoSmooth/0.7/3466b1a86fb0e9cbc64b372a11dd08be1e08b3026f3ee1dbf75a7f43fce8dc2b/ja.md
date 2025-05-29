```
loo_from_psis(
    log_likelihood::AbstractArray{<:Real}, psis_object::Psis; 
    chain_index::Vector{<:Integer}
)
```

事前に計算された `Psis` オブジェクトを使用して、leave-one-out クロスバリデーションスコアを推定します。

# 引数

  * `log_likelihood::Array`: ログ尤度値の行列または3次元配列で、次のようにインデックス付けされています。

`[data, step, chain]`。`chain` 引数は、`chain_index` が提供されている場合や、すべての事後サンプルが単一のチェーンから引き出された場合は省略できます。

  * `psis_object`: LOO-CV スコアを推定するために使用される事前計算された `Psis` オブジェクト。
  * `chain_index::Vector{Int}`: 各ステップがどのチェーンに属するかを指定する整数のオプションベクター。

たとえば、`chain_index[step]` は、`log_likelihood[:, step]` が第二のチェーンに属する場合は `2` を返すべきです。

参照: [`psis`](@ref), [`loo`](@ref), [`PsisLoo`](@ref)。
