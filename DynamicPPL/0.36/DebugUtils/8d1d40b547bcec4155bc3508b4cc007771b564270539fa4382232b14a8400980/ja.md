```
check_model_and_trace([rng, ]model::Model; kwargs...)
```

`model`が有効であることを確認し、潜在的な問題について警告します。

これは、以下の問題についてモデルをチェックします：

1. モデル内で同じvarnameを繰り返し使用している。
2. 変数を固定ではなくランダムとして誤って扱っている、またはその逆。

# 引数

  * `rng::Random.AbstractRNG`: モデルを評価する際に使用する乱数生成器。
  * `model::Model`: チェックするモデル。

# キーワード引数

  * `varinfo::VarInfo`: モデルを評価する際に使用するvarinfo。デフォルト: `VarInfo(model)`。
  * `context::AbstractContext`: モデルを評価する際に使用するコンテキスト。デフォルト: [`DefaultContext`](@ref)。
  * `error_on_failure::Bool`: モデルチェックが失敗した場合にエラーをスローするかどうか。デフォルト: `false`。

# 戻り値

  * `issuccess::Bool`: モデルチェックが成功したかどうか。
  * `trace::Vector{Stmt}`: モデルチェック中に実行されたステートメントのトレース。

# 例

## 正しいモデル

```jldoctest check-model-and-tracecheck-model-and-trace; setup=:(using Distributions)
julia> using StableRNGs

julia> rng = StableRNG(42);

julia> @model demo_correct() = x ~ Normal()
demo_correct (generic function with 2 methods)

julia> issuccess, trace = check_model_and_trace(rng, demo_correct());

julia> issuccess
true

julia> print(trace)
 assume: x ~ Normal{Float64}(μ=0.0, σ=1.0) ⟼ -0.670252 (logprob = -1.14356)

julia> issuccess, trace = check_model_and_trace(rng, demo_correct() | (x = 1.0,));
┌ Warning: モデルにはパラメータが含まれていません。
└ @ DynamicPPL.DebugUtils DynamicPPL.jl/src/debug_utils.jl:342

julia> issuccess
true

julia> print(trace)
observe: 1.0 ~ Normal{Float64}(μ=0.0, σ=1.0) (logprob = -1.41894)
```

## 不正なモデル

```jldoctest check-model-and-tracecheck-model-and-trace; setup=:(using Distributions)
julia> @model function demo_incorrect()
           # (×) `x`を2回サンプリングすると不正確な対数確率が生じます！
           x ~ Normal()
           x ~ Exponential()
       end
demo_incorrect (generic function with 2 methods)

julia> issuccess, trace = check_model_and_trace(rng, demo_incorrect(); error_on_failure=true);
ERROR: varname xがモデル内で複数回使用されています
```
