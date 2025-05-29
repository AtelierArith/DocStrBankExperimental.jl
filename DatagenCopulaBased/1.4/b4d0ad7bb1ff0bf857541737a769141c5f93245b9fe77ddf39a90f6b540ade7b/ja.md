```
NestedClaytonCopula
```

フィールド:

  * children::Vector{ClaytonCopula}  子コピュラのベクター
  * m::Int ≧ 0 - 親コピュラによってのみモデル化される追加の周辺変数の数
  * θ::Real - 親コピュラのパラメータ、ドメイン θ > 0。

ネストされたクレイトンコピュラ: C*θ(C*ϕ₁(u₁₁, ..., u₁,ₙ₁), ..., C_ϕₖ(uₖ₁, ..., uₖ,ₙₖ), u₁ , ... uₘ)。もし m > 0 であれば、最後の m 変数は親コピュラによってのみモデル化されます。

コンストラクタ

```
NestedClaytonCopula(children::Vector{ClaytonCopula}, m::Int, θ::Real)
```

ϕ を子コピュラのパラメータのベクターとすると、十分なネスティング条件は θ <= 最小(ϕ) を要求します。

コンストラクタ

```
NestedClaytonCopula(children::Vector{ClaytonCopula}, m::Int, θ::Real, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するために、空の型 cor::Type{<:CorrelationType} を使用します。ここで、SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。cor を使用する場合、コンストラクタ内の θ の位置に期待される相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。

```jldoctest
julia> a = ClaytonCopula(2, 2.)
ClaytonCopula(2, 2.0)

julia> NestedClaytonCopula([a], 2, 0.5)
NestedClaytonCopula(ClaytonCopula[ClaytonCopula(2, 2.0)], 2, 0.5)

julia> NestedClaytonCopula([a, a], 2, 0.5)
NestedClaytonCopula(ClaytonCopula[ClaytonCopula(2, 2.0), ClaytonCopula(2, 2.0)], 2, 0.5)

```
