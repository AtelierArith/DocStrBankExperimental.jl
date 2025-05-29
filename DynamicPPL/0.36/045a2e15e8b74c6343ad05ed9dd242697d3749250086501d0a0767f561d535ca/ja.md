```
extract_priors([rng::Random.AbstractRNG, ]model::Model)
```

モデルから事前分布を抽出します。

これは、モデルからサンプリングを行い、サンプルを生成するために使用される分布を記録することによって行われます。

!!! warning
    抽出はモデルの実行によって行われるため、いくつかの注意点があります：

    1. もしある変数が `y ~ Normal(0, x)` のように、`x ~ Normal()` もランダム変数である場合、抽出された事前分布は毎回異なるパラメータを持ちます！
    2. モデルが静的サポートを持たない場合、例えば `n ~ Categorical(1:10); x ~ MvNormmal(zeros(n), I)` のように、抽出された事前分布自体が抽出ごとに異なり、パラメータだけでなくなります。

    これらの注意点は以下に示されています。


# 例

## パラメータの変更

```jldoctest
julia> using Distributions, StableRNGs

julia> rng = StableRNG(42);

julia> @model function model_dynamic_parameters()
           x ~ Normal(0, 1)
           y ~ Normal(x, 1)
       end;

julia> model = model_dynamic_parameters();

julia> extract_priors(rng, model)[@varname(y)]
Normal{Float64}(μ=-0.6702516921145671, σ=1.0)

julia> extract_priors(rng, model)[@varname(y)]
Normal{Float64}(μ=1.3736306979834252, σ=1.0)
```

## サポートの変更

```jldoctest
julia> using LinearAlgebra, Distributions, StableRNGs

julia> rng = StableRNG(42);

julia> @model function model_dynamic_support()
           n ~ Categorical(ones(10) ./ 10)
           x ~ MvNormal(zeros(n), I)
       end;

julia> model = model_dynamic_support();

julia> length(extract_priors(rng, model)[@varname(x)])
6

julia> length(extract_priors(rng, model)[@varname(x)])
9
```
