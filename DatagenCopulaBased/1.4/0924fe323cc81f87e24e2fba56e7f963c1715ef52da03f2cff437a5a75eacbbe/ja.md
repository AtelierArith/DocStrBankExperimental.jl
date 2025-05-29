```
AmhCopulaRev
```

フィールド:

  * n::Int - マージナルの数
  * θ::Real - パラメータ

コンストラクタ

```
AmhCopulaRev(n::Int, θ::Real)
```

θでパラメータ化された逆アリ・ミハイル・ハクコピュラ、すなわち出力が1 .- uであり、uは対応するAMHコピュラによってモデル化される。ドメイン: θ ∈ (0, 1) で n > 2 および θ ∈ [-1, 1] で n = 2。

コンストラクタ

```
AmhCopulaRev(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するために、空の型 cor::Type{<:CorrelationType} を使用します。ここで、SpearmanCorrelation <:CorrelationType および KendallCorrelation<:CorrelationType です。corを使用する場合は、コンストラクタ内のθの場所に期待される相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。このような相関はゼロより大きく、θのドメインにより上限が制限されなければなりません。               - スピアマン相関は範囲(0, 0.5)内でなければならない               - ケンドール相関は範囲(0, 1/3)内でなければならない

```jldoctest
julia> AmhCopulaRev(4, .3)
AmhCopulaRev(4, 0.3)
```
