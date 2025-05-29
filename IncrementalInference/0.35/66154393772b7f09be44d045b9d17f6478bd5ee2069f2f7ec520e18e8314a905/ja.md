```julia
struct Mixture{N, F<:DistributedFactorGraphs.AbstractFactor, S, T<:Tuple} <: DistributedFactorGraphs.AbstractFactor
```

`Mixture`オブジェクトは、`<: AbstractPrior`または`<: AbstractRelative`のいずれかで使用されます。

ノート

  * 内部データ表現は`::NamedTuple`であり、すべてのコンポーネントタイプに対して完全な型安定性を提供します。
  * 様々な構築ヘルパーは、`<: AbstractArray`や`Tuple`を含む多様な入力を受け入れることができます。
  * `N`は混合を作成するために使用されるコンポーネントの数であり、したがって、2つのノーマルコンポーネントからの2つのバンプは`N=2`を意味します。

開発ノート

  * FIXME APIの順序を入れ替えて、Mixtureが分布のように機能するようにします。Caesar.jl #808

      * フィールドメカニクスを持つべきではありません。
  * TODO サンプリングについては#1099、#1094、#1069を参照してください。

例

```julia
# prior factor
msp = Mixture(Prior, 
              [Normal(0,0.1), Uniform(-pi/1,pi/2)],
              [0.5;0.5])

addFactor!(fg, [:head], msp, tags=[:MAGNETOMETER;])

# Or relative
mlr = Mixture(LinearRelative, 
              (correlator=AliasingScalarSampler(...), naive=Normal(0.5,5), lucky=Uniform(0,10)),
              [0.5;0.4;0.1])

addFactor!(fg, [:x0;:x1], mlr)
```
