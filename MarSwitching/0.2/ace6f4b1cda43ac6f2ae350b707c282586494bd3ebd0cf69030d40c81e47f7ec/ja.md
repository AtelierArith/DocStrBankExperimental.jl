```
state_coeftable(model::MSM, state::Int64; digits::Int64=3)
```

指定された状態の係数とその統計のフォーマットされたテーブルを返します。これは `summary_msm` 関数によって呼び出される関数の一つです。

他にも [`summary_msm`](@ref)、[`coeftable_tvtp`](@ref)、[`transition_mat`](@ref) を参照してください。
