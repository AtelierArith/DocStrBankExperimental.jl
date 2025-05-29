```julia
MQGP(
    samples::AbstractArray{<:@NamedTuple{x::Tuple{Vector{Float64}, Int64}, y::Float64}};
    bounds,
    N,
    kernel,
    means_use,
    means_learn,
    noise_value,
    noise_learn,
    use_cond_pdf
) -> MultiQuantityGPs.MQGP{typeof(MultiQuantityGPs.Kernels.multiKernel)}

```

与えられたサンプルに基づいてトレーニングされ、条件付けされたハイパーパラメータを持つMQGPを作成して返します。下限と上限は、ハイパーパラメータの1つを初期化するために使用されます。

ノイズの標準偏差は、すべてのサンプルに対して単一のスカラー値として、または各サンプルに対して1つの値を持つベクトルとしてオプションで渡すことができます。

# 例

```julia
# MQGPを作成する
beliefModel = MQGP([prior_samples; samples]; bounds)
```
