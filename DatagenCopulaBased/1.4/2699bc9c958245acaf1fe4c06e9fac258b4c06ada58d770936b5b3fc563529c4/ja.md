```
ClaytonCopulaRev
```

フィールド:

  * n::Int - マージナルの数
  * θ::Real - パラメータ

コンストラクタ

```
ClaytonCopulaRev(n::Int, θ::Real)
```

θ::Real でパラメータ化された逆クレイトンコピュラ（逆とは u → 1 .- u を意味します）。ドメイン: θ ∈ (0, ∞) で n > 2 および θ ∈ [-1, 0) ∪ (0, ∞) で n = 2、n::Int ≧ 2 に対してサポートされています。

コンストラクタ

```
ClaytonCopulaRev(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するために、空の型 cor::Type{<:CorrelationType} を使用します。ここで、SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。cor を使用する場合は、コンストラクタ内の θ の位置に期待される相関を置きます。そうするとコピュラパラメータが計算されます。相関はゼロより大きくなければなりません。

```jldoctest

julia> ClaytonCopulaRev(4, 3.)
ClaytonCopulaRev(4, 3.0)

julia> ClaytonCopulaRev(4, 0.9, SpearmanCorrelation)
ClaytonCopulaRev(4, 5.5595567742323775)

```
