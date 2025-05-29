```
DoubleNestedGumbelCopula
```

フィールド:

  * children::Vector{Nested _Gumbel _cop}  子コピュラのベクター
  * θ::Real - 親コピュラのパラメータ、ドメイン θ ∈ [1,∞)。

コンストラクタ

```
Double_Nested_Gumbel _cop(children::Vector{NestedGumbelCopula}, θ::Real)
```

θと子コピュラの十分なネスティング条件が必要です。

コンストラクタ

```
Doulbe_NestedGumbelCopula(children::Vector{NestedGumbelCopula}, θ::Real, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するには、空の型 cor::Type{<:CorrelationType} を使用します。ここで、SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。cor を使用する場合は、コンストラクタ内の θ の位置に期待される相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。

```jldoctest

julia> a = GumbelCopula(2, 5.)
GumbelCopula(2, 5.0)

julia> b = GumbelCopula(2, 6.)
GumbelCopula(2, 6.0)

julia> c = GumbelCopula(2, 5.5)
GumbelCopula(2, 5.5)

julia> p1 = NestedGumbelCopula([a,b], 1, 2.)
NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 5.0), GumbelCopula(2, 6.0)], 1, 2.0)

julia> p2 = NestedGumbelCopula([c], 2, 2.1)
NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 5.5)], 2, 2.1)

julia> DoubleNestedGumbelCopula([p1, p2], 1.5)
DoubleNestedGumbelCopula(NestedGumbelCopula[NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 5.0), GumbelCopula(2, 6.0)], 1, 2.0), NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 5.5)], 2, 2.1)], 1.5)
```
