```
abstract type Connective <: Syntactical end
```

[論理接続詞](https://en.wikipedia.org/wiki/Logical_connective)のための抽象型で、非原子的な文を表現するために使用されます。例えば、CONJUNCTION、DISJUNCTION、NEGATION、IMPLICATION（スタイライズされた記号として∧、∨、¬、→）があります。

# 実装

接続詞の新しい型 `C` を実装する際は、その `arity` を定義してください。例えば、二項演算子（例：∨または∧）の場合：

```
arity(::C) = 2
```

アリティが1より大きい*可換*接続詞の新しい型 `C` を実装する際は、`iscommutative(::C)` メソッドを提供してください。これによりモデルチェック操作が高速化される可能性があります。

カスタム二項接続詞を実装する場合、デフォルトの `precedence` と `associativity` をオーバーライドすることができます（詳細は[こちら](https://docs.julialang.org/en/v1/manual/mathematical-operations/#Operator-Precedence-and-Associativity)を参照）。カスタム接続詞が `NamedConnective` であり、`math symbol`（例えば、`⊙`、詳細は https://stackoverflow.com/a/60321302/5646732 を参照）として表示される場合、Juliaパーサーによって `Base.operator_precedence` と `Base.operator_associativity` がこれらの動作を定義するために使用され、これらのメソッドを提供しない方が良いかもしれません。

*命題*接続詞の意味論は `collatetruth` を介して指定できます（以下の例を参照）。原則として、定義は真理値間の部分順序（`precedes` を介して指定）に依存することができます。

以下は、xor (⊻) ブール演算子のカスタム実装の例です。

```julia
import SoleLogics: arity, iscommutative, collatetruth
const ⊻ = SoleLogics.NamedConnective{:⊻}()
SoleLogics.arity(::typeof(⊻)) = 2
SoleLogics.iscommutative(::typeof(⊻)) = true
SoleLogics.collatetruth(::typeof(⊻), (t1, t2)::NTuple{N,T where T<:BooleanTruth}) where {N} = (count(istop, (t1, t2)) == 1)
```

`collatetruth` は、少なくともいくつかの真理値型 `T` に対して、`NTuple{arity,T}` を第二引数として受け入れるメソッドで定義されなければならないことに注意してください。

演算子が不完全な解釈（例：原子の `Truth` 値が不明な場合）で機能するようにするために、`NTuple{arity,T where T<:Formula}` に対する簡略化ルールを `simplify` のメソッドを介して提供する必要があります。例えば、これらのルールは `TOP/`BOT` の間のxorを簡略化するのに十分です。

```julia
import SoleLogics: simplify
simplify(::typeof(⊻), (t1, t2)::Tuple{BooleanTruth,BooleanTruth}) = istop(t1) == istop(t2) ? BOT : TOP
simplify(::typeof(⊻), (t1, t2)::Tuple{BooleanTruth,Formula}) = istop(t1) ? ¬t2 : t2
simplify(::typeof(⊻), (t1, t2)::Tuple{Formula,BooleanTruth}) = istop(t2) ? ¬t1 : t1
```

ディスパッチの曖昧さに注意してください！

[`arity`](@ref)、[`SyntaxBranch`](@ref)、[`associativity`](@ref)、[`precedence`](@ref)、[`check`](@ref)、[`iscommutative`](@ref)、[`NamedConnective`](@ref)、[`Syntactical`](@ref) も参照してください。
