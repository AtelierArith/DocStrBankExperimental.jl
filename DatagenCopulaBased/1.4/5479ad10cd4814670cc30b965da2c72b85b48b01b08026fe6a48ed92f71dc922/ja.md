```
GumbelCopula
```

フィールド:

  * n::Int - マージナルの数
  * θ::Real - パラメータ

コンストラクタ

```
    GumbelCopula(n::Int, θ::Real)
```

Gumbel n変量コピュラは、θ::Real ∈ [1, ∞) でパラメータ化され、n::Int ≧ 2 に対してサポートされています。

コンストラクタ

```
GumbelCopula(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

期待相関からコピュラパラメータを計算するには、空の型 cor::Type{<:CorrelationType} を使用します。ここで、SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。cor を使用する場合は、コンストラクタ内の θ の位置に期待相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。

```jldoctest

julia> GumbelCopula(4, 3.)
GumbelCopula(4, 3.0)

julia> GumbelCopula(4, .75, KendallCorrelation)
GumbelCopula(4, 4.0)
```
