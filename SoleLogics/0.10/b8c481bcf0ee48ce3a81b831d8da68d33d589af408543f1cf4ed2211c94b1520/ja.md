```
function randformula(
    [T::Type{<:Formula}=SyntaxTree,]
    [rng::Union{Integer,AbstractRNG}=Random.GLOBAL_RNG,]
    height::Integer,
    alphabet::Union{AbstractVector,AbstractAlphabet},
    operators::AbstractVector{<:Operator},
    args...;
    modaldepth::Integer=height,
    atompicker::Union{Nothing,Function,AbstractWeights,AbstractVector{<:Real}}=randatom,
    opweights::Union{Nothing,AbstractWeights,AbstractVector{<:Real}}=nothing,
    alphabet_sample_kwargs::Union{Nothing,AbstractVector}=nothing,
    kwargs...
)
```

擬似ランダムな型[`T`](@ref)の数式を返します。

# 引数

  * `rng::Union{Intger,AbstractRNG}=Random.GLOBAL_RNG`: 擬似乱数生成器;
  * `height::Integer`: 生成される構造の高さ;
  * `alphabet::AbstractAlphabet`: 原子がランダムに選ばれるコレクション;
  * `operators::AbstractVector{<:Operator}`: 合法的な演算子が選ばれるベクター。

# キーワード引数

  * `modaldepth::Integer`: 最大モーダル深度;
  * `atompicker::Union{Nothing,Function,AbstractWeights,AbstractVector{<:Real}}`: ランダムな要素を選ぶために使用されるメソッド。例えば、これはBase.rand、StatsBase.sample、または整数の配列や`StatsBase.AbstractWeights`の配列である可能性があります;
  * `opweights::Union{Nothing,AbstractWeights,AbstractVector{<:Real}}`: 演算子はこのベクターに比例した確率でサンプリングされます（StatsBaseパッケージの[`AbstractWeights`](@ref)を参照）。
  * `alphabet_sample_kwargs::AbstractVector`: 与えられたアルファベットが有限でない場合に引き出す原子のプール。

# 例

```julia-repl
julia> syntaxstring(randformula(4, ExplicitAlphabet([1,2]), [NEGATION, CONJUNCTION, IMPLICATION]))
"¬((¬(¬(2))) → ((1 → 2) → (1 → 2)))"
```

他にも[`AbstractAlphabet`](@ref)、[`AbstractWeights`](@ref)、[`Atom`](@ref)、[`Operator`](@ref)、[`SyntaxBranch`](@ref)、[`SyntaxTree`](@ref)を参照してください。
