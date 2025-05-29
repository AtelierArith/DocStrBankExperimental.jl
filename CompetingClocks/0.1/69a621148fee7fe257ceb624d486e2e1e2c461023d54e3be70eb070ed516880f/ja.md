```
MultiSampler{SamplerKey,Key,Time}(which_sampler::Function)
```

これは、次に発火する遷移を決定するために複数の確率的サンプリングアルゴリズム（SSA）を使用するサンプラーを作成します。すべてのアルゴリズムの中で最も早い遷移を返します。`which_sampler`関数は、クロックIDまたはキーを見て、このクロックをサンプリングするサンプラーを選択します。このサンプラーにアルゴリズムを追加するには、辞書に追加するのと同じようにします。

クロックが最初に有効化されると、それは常に同じサンプラーに向かいます。このサンプラーは関連付けを記憶しており、半無限のクロックを持つシミュレーションではメモリが増加する可能性があります。

# 例

指数分布用のサンプラーを1つ、いくつかの速いクロック用のサンプラーを1つ、遅いクロック用のサンプラーを1つ作成しましょう。これらにシンボルで名前を付けることができます。コツは、各種分布を正しいサンプラーに向ける必要があることです。時間にはFloat64を使用し、各クロックはInt64で識別できます。

```
using CompetingClocks
using Distributions: Exponential, UnivariateDistribution

struct ByDistribution <: SamplerChoice{Int64,Symbol} end

function CompetingClocks.choose_sampler(
    chooser::ByDistribution, clock::Int64, distribution::Exponential
    )::Symbol
    return :direct
end
function CompetingClocks.choose_sampler(
    chooser::ByDistribution, clock::Int64, distribution::UnivariateDistribution
    )::Symbol
    if clock < 100
        return :fast
    else
        return :slow
    end
end
sampler = MultiSampler{Symbol,Int64,Float64}(ByDistribution())
sampler[:direct] = OptimizedDirect{Int64,Float64}()
sampler[:fast] = FirstToFire{Int64,Float64}()
sampler[:slow] = FirstToFire{Int64,Float64}()
```
