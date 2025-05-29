```
function psis_loo(
    log_likelihood::AbstractArray{<:Real} [, args...];
    [, chain_index::Vector{Int}, kwargs...]
) -> PsisLoo
```

パレート平滑化重要度サンプリングを使用して、留一交差検証スコアを計算します。

# 引数

  * `log_likelihood::Array`: ログ尤度値の行列または3次元配列で、次のようにインデックス付けされます

`[data, step, chain]`。`chain_index`が提供されている場合、またはすべての事後サンプルが単一のチェーンから引き出された場合は、チェーン引数を省略できます。

  * `args...`: [`psis`](@ref)に渡される位置引数。
  * `chain_index::Vector{Int}`: 各ステップがどのチェーンに属するかを指定する整数のオプションベクター。たとえば、`chain_index[step]`は、`log_likelihood[:, step]`が第2チェーンに属する場合は`2`を返すべきです。
  * `kwargs...`: [`psis`](@ref)に渡されるキーワード引数。

参照: [`psis`](@ref), [`loo`](@ref), [`PsisLoo`](@ref).
