```
DataFrame <: AbstractDataFrame
```

名前付き列のセットを格納する `AbstractDataFrame` です。

列は通常、メモリに格納された `AbstractVector` であり、特に `Vector`、`PooledVector` または `CategoricalVector` です。

# コンストラクタ

```julia
DataFrame(pairs::Pair...; makeunique::Bool=false, copycols::Bool=true)
DataFrame(pairs::AbstractVector{<:Pair}; makeunique::Bool=false, copycols::Bool=true)
DataFrame(ds::AbstractDict; copycols::Bool=true)
DataFrame(; kwargs..., copycols::Bool=true)

DataFrame(table; copycols::Union{Bool, Nothing}=nothing)
DataFrame(table, names::AbstractVector;
          makeunique::Bool=false, copycols::Union{Bool, Nothing}=nothing)
DataFrame(columns::AbstractVecOrMat, names::AbstractVector;
          makeunique::Bool=false, copycols::Bool=true)

DataFrame(::DataFrameRow; copycols::Bool=true)
DataFrame(::GroupedDataFrame; copycols::Bool=true, keepkeys::Bool=true)
```

# キーワード引数

  * `copycols` : 列として渡されたベクトルをコピーするかどうか; デフォルトは `true` に設定されており、ベクトルはコピーされます; `false` に設定すると、`DataFrame` を新しい列を生成せずに構築することができない場合は、渡された列がコピーされます。`Tables.jl` 互換のコンストラクタでは `copycols=nothing` のデフォルトが提供されており、特定の入力テーブルタイプはすでに列のコピーを作成しているか、列が不変である可能性があるため、デフォルトでは列はコピーされません。そのような場合に強制的にコピーを行うには、または不変の入力テーブル（例えば `Arrow.Table`）から可変の列を取得するには、明示的に `copycols=true` を渡してください。
  * `makeunique` : `false` の場合（デフォルト）、エラーが発生します

（すべてのコンストラクタがこれらのキーワード引数をサポートしているわけではありません）

# 異なるコンストラクタの動作に関する詳細

`Pair` のベクトル、`Pair` のリストを位置引数として渡すこと、またはキーワード引数のリストを渡すことが許可されています。この場合、各ペアは列名と列値のマッピングを表すものと見なされ、列名は `Symbol` または文字列でなければなりません。あるいは、コンストラクタに辞書を渡すこともでき、その場合はそのエントリが列名と列値のペアを定義するものと見なされます。辞書が `Dict` の場合、列名は返される `DataFrame` でソートされます。

上記のすべてのコンストラクタでは、列値はそのまま消費されるベクトルであるか、他の任意の型のオブジェクト（`AbstractArray` を除く）であることができます。後者の場合、渡された値は自動的に適切な長さの新しいベクトルを埋めるために繰り返されます。特定のルールとして、`Ref` または `0` 次元の `AbstractArray` に格納された値はアンラップされ、同じように扱われます。

ベクトルのベクトルまたは行列を最初の引数として渡すことも許可されています。この場合、2 番目の引数は列名を指定する `Symbol` または文字列のベクトルでなければならず、または自動的に列名 `x1`、`x2`、... を生成するためのシンボル `:auto` でなければなりません。この場合、最初の引数が行列であり、`copycols=false` の場合、作成された `DataFrame` の列は元の行列の列のビューになります。

`DataFrame` コンストラクタに単一の位置引数が渡されると、それは [Tables.jl](https://github.com/JuliaData/Tables.jl) インターフェースを実装する型であると見なされ、返される `DataFrame` が具現化されます。

2 つの位置引数が渡され、2 番目の引数が `AbstractVector` の場合、最初の引数は前の段落で説明したテーブルと見なされ、結果のデータフレームの列名は2 番目の位置引数として渡されたベクトルから取得されます。

最後に、`DataFrameRow` または `GroupedDataFrame` から `DataFrame` を構築することも許可されています。後者の場合、`keepkeys` キーワード引数は、結果の `DataFrame` が渡された `GroupedDataFrame` のグループ化列を含むべきかどうかを指定し、結果の行の順序は渡された `GroupedDataFrame` のグループの順序に従います。

# 注意事項

`DataFrame` コンストラクタはデフォルトで渡されたすべての列ベクトルをコピーします。ベクトルをコピーせずに再利用するには、`copycols=false` キーワード引数を渡してください（サポートされている場合）。

デフォルトでは、列名に重複が見つかった場合、エラーが発生します。重複名を受け入れるには、`makeunique=true` キーワード引数を渡してください（サポートされている場合）。この場合、重複名には `_i` がサフィックスとして付加されます（`i` は最初の重複のために 1 から始まります）。

`AbstractRange` が列として `DataFrame` コンストラクタに渡されると、常に `Vector` に収集されます（`copycols=false` の場合でも）。一般的なルールとして、`AbstractRange` の値はすべて、`DataFrame` に格納される前に DataFrames.jl のすべての関数によって `Vector` に具現化されます。

`DataFrame` は 1 ベースのインデックスを使用する列のみを格納できます。非標準のインデックスを使用するベクトルを格納しようとするとエラーが発生します。

`DataFrame` 型は、列の型が異なることを許可し、構築後も動的に変更できるように設計されています。したがって、`DataFrame` は型安定ではありません。型安定性が必要なパフォーマンスクリティカルなコードには、`select` / `transform` / `combine` 関数が提供する機能を使用するか、`Tables.columntable` および `Tables.namedtupleiterator` 関数を使用するか、バリア関数を使用するか、`DataFrame` から抽出された列を保持する変数に型アサーションを提供してください。

メタデータ: この関数はすべてのテーブルおよび列レベルのメタデータを保持します。特別なケースとして、`GroupedDataFrame` が渡された場合、親の `GroupedDataFrame` からの `:note` スタイルのメタデータのみが保持されます。

# 例

```jldoctest
julia> DataFrame((a=[1, 2], b=[3, 4])) # Tables.jl テーブルコンストラクタ
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      4

julia> DataFrame([(a=1, b=0), (a=2, b=0)]) # Tables.jl テーブルコンストラクタ
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame("a" => 1:2, "b" => 0) # Pair コンストラクタ
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame([:a => 1:2, :b => 0]) # Pairs のベクトルコンストラクタ
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame(Dict(:a => 1:2, :b => 0)) # 辞書コンストラクタ
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame(a=1:2, b=0) # キーワード引数コンストラクタ
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame([[1, 2], [0, 0]], [:a, :b]) # ベクトルのベクトルコンストラクタ
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame([1 0; 2 0], :auto) # 行列コンストラクタ
2×2 DataFrame
 Row │ x1     x2
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0
```
