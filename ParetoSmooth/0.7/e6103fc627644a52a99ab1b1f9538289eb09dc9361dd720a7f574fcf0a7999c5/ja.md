```
psis!(
    is_ratios::AbstractVector{<:Real}; 
    tail_length::Integer, log_weights::Bool=true
) -> Real
```

単一のベクトルに対してPSISを実行し、推定された`pareto_k`分布の形状定数を返す前に、その尾の値を*インプレース*で平滑化します。これは*ログ重み*を正規化しません。

# 引数

  * `is_ratios::AbstractVector{<:Real}`: 最大値が1になるようにスケーリングされた重要度サンプリング比のベクトル。
  * `r_eff::AbstractVector{<:Real}`: 有効サンプルサイズを計算するために使用される相対的有効サンプルサイズ。詳細については[rel_eff](@ref)を参照してください。
  * `log_weights::Bool`: 入力ベクトルが生の重要度サンプリング比ではなく、ログ比のベクトルであるかどうかを示すブール値。

# 戻り値

  * `Real`: ξ、GPDの形状パラメータ。大きな数値は太い尾を示します。

# 注意事項

配列に対するメソッドとは異なり、`psis!`は入力値が有効であることを確認するためのチェックを行いません。
