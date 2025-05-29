```
randformula(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG, ]
    height::Integer,
    alphabet,
    operators::AbstractVector;
    kwargs...
)::SyntaxTree

randformula(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG, ]
    height::Integer,
    g::AbstractGrammar;
    kwargs...
)::SyntaxTree
```

擬似乱数の `SyntaxTree` を返します。

# 引数

  * `rng::Union{Intger,AbstractRNG} = Random.GLOBAL_RNG`: 擬似乱数生成器;
  * `height::Integer`: 生成される構造の高さ;
  * `alphabet::AbstractAlphabet`: 原子がランダムに選ばれるコレクション;
  * `operators::AbstractVector`: 法則的な演算子が選ばれるベクトル;
  * `g::AbstractGrammar`: アルファベットと演算子を別々に渡す代替手段。(TODO 説明?)

# キーワード引数

  * `modaldepth::Integer`: 最大モーダル深度
  * `atompicker::Function`: ランダムな要素を選ぶために使用されるメソッド。例えば、これは Base.rand または StatsBase.sample である可能性があります。
  * `opweights::AbstractWeights`: 演算子のセットに対する重みベクトル（`StatsBase` を参照）。

# 例

```julia-repl
julia> syntaxstring(randformula(4, ExplicitAlphabet([1,2]), [NEGATION, CONJUNCTION, IMPLICATION]))
"¬((¬(¬(2))) → ((1 → 2) → (1 → 2)))"
```

[`AbstractAlphabet`](@ref) や [`SyntaxBranch`](@ref) も参照してください。
