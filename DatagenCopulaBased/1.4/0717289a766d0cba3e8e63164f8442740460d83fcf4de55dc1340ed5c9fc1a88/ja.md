```
ネストされたガンベルコピュラ
```

フィールド:

  * children::Vector{GumbelCopula}  子コピュラのベクター
  * m::Int ≧ 0 - 親コピュラのみでモデル化される追加の周辺変数の数
  * θ::Real - 親コピュラのパラメータ、ドメイン θ ∈ [1,∞)。

ネストされたガンベルコピュラ: C _θ(C _ϕ₁(u₁₁, ..., u₁,ₙ₁), ..., C _ϕₖ(uₖ₁, ..., uₖ,ₙₖ), u₁ , ... uₘ)。もし m > 0 であれば、最後の m 変数は親コピュラのみでモデル化されます。

コンストラクタ

```
NestedGumbelCopula(children::Vector{GumbelCopula}, m::Int, θ::Real)
```

ϕ を子コピュラのパラメータのベクターとすると、十分なネスティング条件は θ <= 最小(ϕ) を要求します。

コンストラクタ

```
NestedGumbelCopula(children::Vector{GumbelCopula}, m::Int, θ::Real, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するために、空の型 cor::Type{<:CorrelationType} を使用します。ここで、SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。cor を使用する場合、コンストラクタ内の θ の位置に期待される相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。

```jldoctest

julia> a = GumbelCopula(2, 5.)
GumbelCopula(2, 5.0)

julia> NestedGumbelCopula([a, a], 2, 2.1)
NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 5.0), GumbelCopula(2, 5.0)], 2, 2.1)
```
