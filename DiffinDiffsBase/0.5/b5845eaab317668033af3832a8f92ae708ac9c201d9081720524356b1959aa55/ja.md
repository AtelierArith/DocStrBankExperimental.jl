```
NeverTreatedParallel{C,S} <: TrendParallel{C,S}
```

サンプル期間中に治療を受けたグループと、サンプル期間中に治療を受けなかったグループの間に平行トレンドの仮定が成り立つと仮定します。詳細は[`nevertreated`](@ref)を参照してください。

# フィールド

  * `e::Tuple{Vararg{ValidTimeType}}`: 治療を受けなかったユニットのグループインデックス。
  * `c::C`: [`ParallelCondition`](@ref)のインスタンス。
  * `s::S`: [`ParallelStrength`](@ref)のインスタンス。
