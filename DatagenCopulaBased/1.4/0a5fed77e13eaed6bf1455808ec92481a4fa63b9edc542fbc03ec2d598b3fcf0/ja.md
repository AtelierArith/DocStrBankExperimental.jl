```
FrankCopula
```

フィールド:

  * n::Int - マージナルの数
  * θ::Real - パラメータ

コンストラクタ

```
FrankCopula(n::Int, θ::Real)
```

θ::Real でパラメータ化された Frank n 次元コピュラ。ドメイン: θ ∈ (0, ∞) は n > 2 の場合、θ ∈ (-∞, 0) ∪ (0, ∞) は n = 2 の場合に対応し、n::Int ≧ 2 に対してサポートされます。

コンストラクタ

```
FrankCopula(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するために、空の型 cor::Type{<:CorrelationType} を使用します。ここで、SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。cor を使用する場合は、コンストラクタ内の θ の場所に期待される相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。

```jldoctest
julia> FrankCopula(2, -5.)
FrankCopula(2, -5.0)

julia> FrankCopula(4, .3)
FrankCopula(4, 0.3)
```
