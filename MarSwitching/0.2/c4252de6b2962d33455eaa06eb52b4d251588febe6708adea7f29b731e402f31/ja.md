```
transition_mat(model::MSM; digits::Int64=2)
```

推定された遷移行列の確率のフォーマットされたテーブルを返します。これは `summary_msm` 関数によって呼び出される関数の一つです。

関連情報としては [`summary_msm`](@ref)、[`state_coeftable`](@ref)、[`coeftable_tvtp`](@ref) があります。
