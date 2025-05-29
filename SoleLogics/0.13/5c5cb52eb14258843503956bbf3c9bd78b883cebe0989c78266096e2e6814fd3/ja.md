```
function randformula(
    [T::Type{<:Formula}=SyntaxTree,]
    [rng::Union{Integer,AbstractRNG}=Random.GLOBAL_RNG,]
    maxheight::Integer,
    alphabet::Union{AbstractVector,AbstractAlphabet},
    operators::AbstractVector{<:Operator},
    args...;
    maxmodaldepth::Integer=maxheight,
    atompicker::Union{Nothing,Function,AbstractWeights,AbstractVector{<:Real}}=randatom,
    opweights::Union{Nothing,AbstractWeights,AbstractVector{<:Real}}=nothing,
    alphabet_sample_kwargs::Union{Nothing,AbstractVector}=nothing,
    kwargs...
)
```

擬似ランダム式を返します [`T`](@ref) の型。

# 引数

  * `rng::Union{Intger,AbstractRNG}=Random.GLOBAL_RNG`: ランダム数生成器;
  * `maxheight::Integer`: 生成される構造の最大高さ;
  * `alphabet::AbstractAlphabet`: 原子がランダムに選ばれるコレクション;
  * `operators::AbstractVector{<:Operator}`: 合法的な演算子が選ばれるベクター。

# キーワード引数

  * `maxmodaldepth::Integer`: 最大モーダル深度;
  * `atompicker::Union{Nothing,Function,AbstractWeights,AbstractVector{<:Real}}`: ランダム要素を選ぶために使用されるメソッド。例えば、これは Base.rand、StatsBase.sample または 整数の配列や `StatsBase.AbstractWeights` の配列である可能性があります;
  * `opweights::Union{Nothing,AbstractWeights,AbstractVector{<:Real}}`: 演算子はこのベクターに比例した確率でサンプリングされます（[`AbstractWeights`](@ref) を参照、StatsBase パッケージの）。
  * `alphabet_sample_kwargs::AbstractVector`: 与えられたアルファベットが有限でない場合に引き出す原子のプール。
  * `basecase::Function` = 再帰の基本ケースを指定するためのメソッド; 指定されていない場合、`atompicker` を返します。

[!WARNING] 基本ケースは再帰の最後に適用されます（すなわち、高さ = 0 のとき）。サブフォーミュラを生成する基本ケースを導入する場合は、`maxheight` パラメータの値を適切に調整してください（例: `o(p,q)` 型のサブフォーミュラを生成する場合、ここで `o` は接続詞であり、`p,q` は原子であるとき、最大高さ `n` のフォーミュラを生成するには、`maxheight` パラメータに `n-1` の値を提供します）。

  * `mode::Bool = :maxheight` は生成される構文木の高さを `maxheight` 以下に制約します（`mode = :maxheight`）、`maxheight` に等しい高さを持つように（`mode = :exactheight`）、または `maxheight` に等しく、完全であるように（`mode = :full`）。
  * `earlystoppingtreshold::Float` : `mode = :maxheight` のとき、到達する前に基本ケースを呼び出す確率を制御します。

# 例

```julia-repl
julia> syntaxstring(randformula(4, ExplicitAlphabet([1,2]), [NEGATION, CONJUNCTION, IMPLICATION]))
"¬((¬(¬(2))) → ((1 → 2) → (1 → 2)))"
```

[`AbstractAlphabet`](@ref)、[`AbstractWeights`](@ref)、[`Atom`](@ref)、[`Operator`](@ref)、[`SyntaxBranch`](@ref)、[`SyntaxTree`](@ref) も参照してください。 ```
