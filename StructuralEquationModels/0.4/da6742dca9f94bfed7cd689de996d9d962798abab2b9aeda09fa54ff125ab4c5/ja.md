観測データに欠損がない場合。

# コンストラクタ

```
SemObservedData(;
    data,
    observed_vars = nothing,
    specification = nothing,
    kwargs...)
```

# 引数

  * `data`: 観測データ – *DataFrame* または *Matrix*
  * `observed_vars::Vector{Symbol}`: データの列名（データとして渡されたオブジェクトに列名がない場合、すなわちデータフレームでない場合）
  * `specification`: オプションのSEM仕様 ([`SemSpecification`](@ref))

# 拡張ヘルプ

## インターフェース

  * `nsamples(::SemObservedData)` -> 観測データポイントの数
  * `nobserved_vars(::SemObservedData)` -> 観測された（顕在）変数の数
  * `samples(::SemObservedData)` -> 観測データ
  * `obs_cov(::SemObservedData)` -> 観測共分散行列
  * `obs_mean(::SemObservedData)` -> 観測平均ベクトル
