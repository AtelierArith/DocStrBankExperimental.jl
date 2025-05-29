```
AmhCopula
```

フィールド:

  * n::Int - マージナルの数
  * θ::Real - パラメータ

コンストラクタ

```
AmhCopula(n::Int, θ::Real)
```

θでパラメータ化されたAli-Mikhail-Haqコピュラ、ドメイン: θ ∈ (0, 1) for n > 2 および θ ∈ [-1, 1] for n = 2.

コンストラクタ

```
AmhCopula(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するために、空の型 cor::Type{<:CorrelationType} を使用します。ここで、SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。cor を使用する場合は、コンストラクタ内の θ の場所に期待される相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。このような相関はゼロより大きく、θのドメインにより上限が制限されなければなりません。             - スピアマン相関は範囲 (0, 0.5) にある必要があります。             - ケンドール相関は範囲 (0, 1/3) にある必要があります。

```jldoctest
julia> AmhCopula(4, .3)
AmhCopula(4, 0.3)

julia> AmhCopula(4, .3, KendallCorrelation)
AmhCopula(4, 0.9999)

```
