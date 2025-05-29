```
unroll(
    moving_average::Vector{Float64},
    window::Int64;
    initial_conditions::U=nothing,
    assert_natural::Bool=false,
) where {U<:Union{Tuple{Vararg{Union{Int64,Float64}}},Nothing}}
```

移動平均 `moving_average` から元の時系列（すなわち、unroll）を取得します。

# 引数

  * `moving_average::Vector{Float64}`: アンロールする移動平均を表す時系列;
  * `window:::Int64`: 移動平均の幅;
  * `initial_conditions::U = nothing`: 復元される元の時系列の初期値。`window-1` の浮動小数点数または整数値の `Tuple` であるか、初期条件が不明な場合は `nothing` である可能性があります;
  * `assert_natural::Bool = false` デフォルトのブール引数。true の場合、パイプラインは自然数のみの時系列を復元しようとします。「受け入れ可能」とは、`moving_average` を再現することを意味し、複数の受け入れ可能な時系列が見つかり、返される可能性があります。

NB: `isnothing(initial_conditions) && !assert_natural` の場合、近似的な方法のみが使用される可能性があります。詳細はこの [StackExchange の投稿](https://stats.stackexchange.com/a/68002) を参照してください。
