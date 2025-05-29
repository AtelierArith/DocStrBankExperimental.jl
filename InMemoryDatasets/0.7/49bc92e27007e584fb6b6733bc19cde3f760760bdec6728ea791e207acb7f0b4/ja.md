```
Dataset <: AbstractDataset
```

名前付き列のセットを格納するAbstractDataset

列は通常、メモリに格納されたAbstractVectorsです。

# コンストラクタ

```julia
Dataset(pairs::Pair...; makeunique::Bool=false)
Dataset(pairs::AbstractVector{<:Pair}; makeunique::Bool=false)
Dataset(ds::AbstractDict)
Dataset(kwargs...)

Dataset(columns::AbstractVecOrMat, names::Union{AbstractVector, Symbol};
          makeunique::Bool=false)

Dataset(table)
Dataset(::DatasetRow)
```

# キーワード引数

  * `makeunique` : `false`（デフォルト）の場合、エラーが発生します

（すべてのコンストラクタがこれらのキーワード引数をサポートしているわけではありません）

# 異なるコンストラクタの動作に関する詳細

`Pair`のベクター、位置引数としての`Pair`のリスト、またはキーワード引数のリストを渡すことが許可されています。この場合、各ペアは列名から列値へのマッピングを表すものと見なされ、列名は`Symbol`または文字列でなければなりません。あるいは、コンストラクタに辞書を渡すこともでき、その場合、辞書のエントリは列名と列値のペアを定義するものと見なされます。辞書が`Dict`である場合、列名は返される`Dataset`内でソートされます。

上記のすべてのコンストラクタでは、列値はそのまま消費されるベクターであるか、他の任意の型のオブジェクト（`AbstractArray`を除く）であることができます。後者の場合、渡された値は自動的に適切な長さの新しいベクターを埋めるために繰り返されます。特に、`Ref`または`0`次元の`AbstractArray`に格納された値はアンラップされ、同じように扱われます。

ベクターのベクターまたは行列を最初の引数として渡すことも許可されています。この場合、2番目の引数は列名を指定する`Symbol`または文字列のベクター、または列名`x1`、`x2`、...を自動的に生成するためのシンボル`:auto`でなければなりません。

`Dataset`コンストラクタに単一の位置引数が渡された場合、それは返される`Dataset`が具現化される[Tables.jl](https://github.com/JuliaData/Tables.jl)インターフェースを実装する型であると見なされます。

最後に、`DatasetRow`から`Dataset`を構築することも許可されています。

# 注意事項

`allowmissing`関数は、出力データセットに追加される前に、コンストラクタに渡されたすべての列に対して呼び出されます。

デフォルトでは、列名に重複が見つかった場合、エラーが発生します。重複名を受け入れるために`makeunique=true`キーワード引数を渡すと（サポートされている場合）、それらには`_i`が接尾辞として付加されます（`i`は最初の重複のために1から始まります）。

`AbstractRange`が列として`Dataset`コンストラクタに渡された場合、それは常に`Vector`に収集されます。一般的なルールとして、`AbstractRange`の値は、`Dataset`に格納される前にInMemoryDatasets.jlのすべての関数によって常に`Vector`に具現化されます。

`Dataset`は1ベースのインデックスを使用する列のみを格納できます。非標準のインデックスを使用するベクターを格納しようとするとエラーが発生します。

`Dataset`型は、列の型が異なることを許可し、構築後も動的に変更できるように設計されています。

# 例

```jldoctest
julia> Dataset((a=[1, 2], b=[3, 4])) # Tables.jl table constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         3
   2 │        2         4

julia> Dataset([(a=1, b=0), (a=2, b=0)]) # Tables.jl table constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset("a" => 1:2, "b" => 0) # Pair constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset([:a => 1:2, :b => 0]) # vector of Pairs constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset(Dict(:a => 1:2, :b => 0)) # dictionary constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset(a=1:2, b=0) # keyword argument constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset([[1, 2], [0, 0]], [:a, :b]) # vector of vectors constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset([1 0; 2 0], :auto) # matrix constructor
2×2 Dataset
 Row │ x1        x2
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0
```
