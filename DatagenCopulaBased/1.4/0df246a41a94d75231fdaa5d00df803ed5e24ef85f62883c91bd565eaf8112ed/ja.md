```
ChainArchimedeanCopulas
```

その後のマージナルのペアは、アーキメデスファミリーからの二変量コピュラによってモデル化されます。サポートされているコピュラは次のとおりです: "Clayton", "Frank", "Ali-Mikhail-Haq", "Gumbel" コピュラはサポートされていません。

フィールド:

  * n::Int - 変数の数
  * θ::Vector{Real} - パラメータのベクトル
  * copulas::Vector{String} - 二変量コピュラを示すベクトル。

可能な要素 "clayton", "frank", "amh"

コンストラクタ

```
ChainArchimedeanCopulas(θ::Vector{Real}, copulas::Vector{String})
```

length(θ) = length(copulas) が必要であり、特定の二変量コピュラに対するθの制限があります。

コンストラクタ

```
ChainArchimedeanCopulas(θ::Vector{Real}, copulas::String)
```

すべての後続のマージナルペアに対して1つのコピュラファミリー。

コンストラクタ

```
ChainArchimedeanCopulas(θ::Vector{Real}, copulas::Vector{String}, cor::Type{<:CorrelationType})

ChainArchimedeanCopulas(θ::Vector{Real}, copulas::String, cor::Type{<:CorrelationType})
```

期待される相関からコピュラパラメータを計算するには、空の型 cor::Type{<:CorrelationType} を使用します。 cor ∈ {SpearmanCorrelation, KendallCorrelation} は、コンストラクタ内のθの代わりにこれらの相関を使用してθを計算します。

すべての場合において n = length(θ)+1 です。

```jldoctest

julia> c = ChainArchimedeanCopulas([4., 11.], "frank")
ChainArchimedeanCopulas(3, [4.0, 11.0], ["frank", "frank"])

julia> c = ChainArchimedeanCopulas([.5, .7], ["frank", "clayton"], "Kendall")
ChainArchimedeanCopulas(3, [5.736282707019972, 4.666666666666666], ["frank", "clayton"])

```
