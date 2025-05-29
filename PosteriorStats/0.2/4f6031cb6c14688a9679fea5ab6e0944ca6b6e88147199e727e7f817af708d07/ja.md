```
summarize(data, stats_funs...; name="SummaryStats", [var_names]) -> SummaryStats
```

`data`の各パラメータに対して、`stats_funs`で指定された要約統計量を計算します。

`stats_funs`は、形状が`(draws, chains)`の行列をスカラーまたはスカラーのコレクションに縮小する関数のコレクションです。あるいは、`stats_funs`の項目は、統計量に使用する名前を指定する`name => fun`の形式の`Pair`であるか、関数がコレクションを返す場合の`(name1, ...) => fun`の形式であることがあります。関数がコレクションを返す場合、この後者の形式の名前を提供する必要があります。

統計関数が提供されていない場合、[`default_summary_stats`](@ref)で指定されたものが計算されます。

`var_names`は、`data`内のパラメータの名前を指定します。提供されない場合、名前は`data`から推測されます。

カスタムオブジェクトから要約統計量を計算するために、このメソッドをオーバーロードして`data`の型を指定します。

他にも[`SummaryStats`](@ref)、[`default_summary_stats`](@ref)、[`default_stats`](@ref)、[`default_diagnostics`](@ref)を参照してください。

# 例

平均、標準偏差、平均推定値のモンテカルロ標準誤差（MCSE）を計算します：

```jldoctest summarize; setup = (using Random; Random.seed!(84))
julia> using Statistics, StatsBase

julia> x = randn(1000, 4, 3) .+ reshape(0:10:20, 1, 1, :);

julia> summarize(x, mean, std, :mcse_mean => sem; name="Mean/Std")
Mean/Std
       mean    std  mcse_mean
 1   0.0003  0.989      0.016
 2  10.02    0.988      0.016
 3  19.98    0.988      0.016
```

`mean_and_std`を使用して平均の再計算を避け、パラメータ名を提供します：

```jldoctest summarize
julia> summarize(x, (:mean, :std) => mean_and_std, mad; var_names=[:a, :b, :c])
SummaryStats
         mean    std    mad
 a   0.000275  0.989  0.978
 b  10.0       0.988  0.995
 c  20.0       0.988  0.979
```

推定量とそのMCSEの両方が計算される場合、MCSEは表示される有効桁数を決定するために使用されることに注意してください。

```jldoctest summarize
julia> summarize(x; var_names=[:a, :b, :c])
SummaryStats
       mean   std  hdi_3%  hdi_97%  mcse_mean  mcse_std  ess_tail  ess_bulk  r ⋯
 a   0.0003  0.99   -1.92     1.78      0.016     0.012      3567      3663  1 ⋯
 b  10.02    0.99    8.17    11.9       0.016     0.011      3841      3906  1 ⋯
 c  19.98    0.99   18.1     21.9       0.016     0.012      3892      3749  1 ⋯
                                                                1列省略
```

すべてのパラメータに対して89%のHDIを持つ統計量のみを計算し、パラメータ名を提供します：

```jldoctest summarize
julia> summarize(x, default_stats(; prob_interval=0.89)...; var_names=[:a, :b, :c])
SummaryStats
         mean    std  hdi_5.5%  hdi_94.5%
 a   0.000275  0.989     -1.63       1.52
 b  10.0       0.988      8.53      11.6
 c  20.0       0.988     18.5       21.6
```

`Statistics.median`に焦点を当てた要約統計量を計算します：

```jldoctest summarize
julia> summarize(x, default_summary_stats(median)...; var_names=[:a, :b, :c])
SummaryStats
    median    mad  eti_3%  eti_97%  mcse_median  ess_tail  ess_median  rhat
 a   0.004  0.978   -1.83     1.89        0.020      3567        3336  1.00
 b  10.02   0.995    8.17    11.9         0.023      3841        3787  1.00
 c  19.99   0.979   18.1     21.9         0.020      3892        3829  1.00
```
