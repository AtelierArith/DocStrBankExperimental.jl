```
ClaytonCopula
```

フィールド:

  * n::Int - マージナルの数
  * θ::Real - パラメータ

コンストラクタ

```
ClaytonCopula(n::Int, θ::Real)
```

θ::Real でパラメータ化された Clayton n 次元コピュラで、n > 2 の場合は θ ∈ (0, ∞)、n = 2 の場合は θ ∈ [-1, 0) ∪ (0, ∞) となり、n::Int ≥ 2 に対してサポートされています。

コンストラクタ

```
ClaytonCopula(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するために、空の型 cor::Type{<:CorrelationType} を使用します。ここで、SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。cor を使用する場合は、コンストラクタ内の θ の場所に期待される相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。

```jldoctest
julia> ClaytonCopula(4, 3.)
ClaytonCopula(4, 3.0)

julia> ClaytonCopula(4, 0.9, SpearmanCorrelation)
ClaytonCopula(4, 5.5595567742323775)
```
