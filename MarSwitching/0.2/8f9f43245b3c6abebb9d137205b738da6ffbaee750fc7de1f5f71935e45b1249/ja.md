```
coeftable_tvtp(model::MSM; digits::Int64=3)
```

TVTPモデルからの推定係数とその統計量のフォーマットされたテーブルを返します。これは`summary_msm`関数によって呼び出される関数の一つです。

関連情報としては、[`summary_msm`](@ref)、[`state_coeftable`](@ref)、[`transition_mat`](@ref)があります。
