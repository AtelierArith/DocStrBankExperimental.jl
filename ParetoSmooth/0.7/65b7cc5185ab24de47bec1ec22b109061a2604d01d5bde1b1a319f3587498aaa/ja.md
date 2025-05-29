```
psis(
    log_ratios::AbstractArray{T<:Real}, 
    r_eff::AbstractVector{T}; 
    source::String="mcmc"    
) -> Psis
```

パレート平滑化重要度サンプリング（PSIS）を実装します。

# 引数

## 位置引数

  * `log_ratios::AbstractArray`: ログスケールでの（非正規化された）重要度比の2次元または3次元配列。インデックスは `[data, step, chain]` の順に並べる必要があります。チェインインデックスは、チェインが1つだけの場合やキーワード引数 `chain_index` が提供されている場合は省略できます。
  * `r_eff::AbstractVector`: ESS計算に使用される相対的有効サンプルサイズの（オプションの）ベクトルです。

空の場合は、InferenceDiagnostics.jlのFFTESSメソッドを使用して自動的に計算されます。これらの値を計算するには `relative_eff` を参照してください。

## キーワード引数

  * `chain_index::Vector{Int}`: 各ステップがどのチェインに属するかを指定する整数のオプションベクトルです。たとえば、`chain_index[step]` は `log_likelihood[:, step]` が第2チェインに属する場合は `2` を返すべきです。
  * `source::String="mcmc"`: 使用されるサンプルのソースを説明する文字列またはシンボルです。`"mcmc"` の場合、自己相関に対してESSを調整します。それ以外の場合、サンプルは独立していると見なされます。現在許可されている値は ["mcmc", "vi", "other"] です。
  * `calc_ess::Bool=true`: `false` の場合、ESS診断を計算しません。ESS診断にアクセスしようとすると、空の配列が返されます。
  * `checks::Bool=true`: `true` の場合、入力に対してエラーの可能性をチェックします。無効にすると、パフォーマンスがわずかに向上します。

また、[`relative_eff`]@ref、[`psis_loo`]@ref、[`psis_ess`]@refも参照してください。
