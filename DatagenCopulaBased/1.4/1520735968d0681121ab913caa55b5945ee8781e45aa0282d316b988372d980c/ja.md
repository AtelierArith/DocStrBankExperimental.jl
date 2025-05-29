```
NestedFrankCopula
```

フィールド:

  * children::Vector{FrankCopula}  子コピュラのベクトル
  * m::Int ≧ 0 - 親コピュラのみでモデル化される追加の周辺変数の数
  * θ::Real - 親コピュラのパラメータ、領域 θ ∈ (0,∞)。

ネストされたフランコピュラ: C _θ(C _ϕ₁(u₁₁, ..., u₁,ₙ₁), ..., C _ϕₖ(uₖ₁, ..., uₖ,ₙₖ), u₁ , ... uₘ)。もし m > 0 の場合、最後の m 変数は親コピュラのみでモデル化されます。

コンストラクタ

```
NestedFrankCopula(children::Vector{FrankCopula}, m::Int, θ::Real)
```

ϕ を子コピュラのパラメータのベクトルとすると、十分なネスティング条件は θ <= 最小(ϕ) を要求します。

コンストラクタ

```
NestedFrankCopula(children::Vector{Frank_ cop}, m::Int, θ::Real, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するために、空の型 cor::Type{<:CorrelationType} を使用します。ここで SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。cor を使用する場合、コンストラクタ内の θ の位置に期待される相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。

```jldoctests

julia> a = FrankCopula(2, 5.)
FrankCopula(2, 5.0)

julia> NestedFrankCopula([a, a], 2, 0.1)
NestedFrankCopula(FrankCopula[FrankCopula(2, 5.0), FrankCopula(2, 5.0)], 2, 0.1)
```
