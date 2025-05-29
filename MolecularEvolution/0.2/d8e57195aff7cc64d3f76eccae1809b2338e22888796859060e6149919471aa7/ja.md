```
metropolis_sample(
    initial_tree::FelNode,
    models::Vector{<:BranchModel},
    num_of_samples;
    bl_sampler::UnivariateSampler = BranchlengthSampler(Normal(0,2), Normal(-1,1))
    burn_in=1000, 
    sample_interval=10,
    collect_LLs = false,
    midpoint_rooting=false,
)
```

便利なメソッドです。メトロポリスアルゴリズムの1ステップは、`softmax_sampler`を使って[`nni_update!`](@ref)を呼び出し、`bl_sampler`を使って[`branchlength_update!`](@ref)を呼び出すことで実行されます。

# 追加の引数

  * `bl_sampler`: 事後分布から枝長を引き出すために使用されるサンプラーです。
