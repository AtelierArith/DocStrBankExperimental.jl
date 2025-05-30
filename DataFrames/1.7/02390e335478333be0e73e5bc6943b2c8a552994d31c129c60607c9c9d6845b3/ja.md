```
groupby(d::AbstractDataFrame, cols;
        sort::Union{Bool, Nothing, NamedTuple}=nothing,
        skipmissing::Bool=false)
```

`AbstractDataFrame`を行グループに分割した`GroupedDataFrame`を返します。

# 引数

  * `df` : 分割する`AbstractDataFrame`
  * `cols` : グループ化するデータフレームの列。任意の列セレクタ（`Symbol`、文字列または整数；`:`, `Cols`, `All`, `Between`, `Not`、正規表現、または`Symbol`、文字列または整数のベクター）を指定できます。特に、セレクタが列を選択しない場合は、単一グループの`GroupedDataFrame`が作成されます。特別なケースとして、`cols`が単一の列または列のベクターである場合、`sort`が`true`の場合にグループの順序を決定するために使用される[`order`](@ref)でラップされた列を含むことができます。`sort`が`false`の場合、`order`を渡すことはエラーです；`sort`が`nothing`の場合、`order`が渡されると`true`に設定されます。
  * `sort` : `sort=true`の場合、グループはグループ化列`cols`の値に従ってソートされます；`sort=false`の場合、グループは`df`内の出現順に作成されます；`sort=nothing`（デフォルト）の場合、最も速い利用可能なグループ化アルゴリズムが選択され、その結果のグループの順序は未定義であり、将来のリリースで変更される可能性があります；以下に現在の実装の説明が提供されています。さらに、`sort`は`alg`、`lt`、`by`、`rev`、および`order`フィールドのいくつかまたはすべてを持つ`NamedTuple`であることもできます。この場合、グループはソートされ、その順序は[`sortperm`](@ref)の順序に従います。
  * `skipmissing` : グループ化列`cols`のいずれかに`missing`値があるグループをスキップするかどうか

# 詳細

`GroupedDataFrame`に対するイテレータは、`df`内の各グループに対して`SubDataFrame`ビューを返します。各グループ内では、`df`内の行の順序が保持されます。

`GroupedDataFrame`は、グループによるインデクシング、`select`、`transform`、および`combine`（各グループに関数を適用し、その結果をデータフレームに結合します）をサポートしています。

`GroupedDataFrame`は辞書インターフェースもサポートしています。キーは[`GroupKey`](@ref)オブジェクトで、[`keys(::GroupedDataFrame)`](@ref)によって返され、各グループのグループ化列の値を取得するためにも使用できます。グループ化列の値を含む`Tuples`および`NamedTuple`（`cols`引数と同じ順序で）もインデックスとして受け入れられます。最後に、キーがデータフレームの列名である`AbstractDict`を使用して、グループ化されたデータフレームにインデックスを付けることができます。この場合、キーの順序は重要ではありません。

現在の実装では、`sort=nothing`の場合、グループはグループ化列の値の出現順に従って順序付けられます。ただし、すべてのグループ化列が非`nothing`の`DataAPI.refpool`を提供する場合は、グループの順序は`DataAPI.refpool`によって返される値の順序に従います。このルールの特定の適用として、すべての`cols`が`CategoricalVector`である場合、グループは常にソートされます。狭い範囲の整数列もこの最適化を使用するため、整数列でグループ化する際のグループの順序は未定義です。列の`eltype`が`Union{Missing, Real}`のサブタイプであり、すべての要素が`missing`であるか`isinteger`テストに合格し、いずれも`-0.0`に等しくない場合、その列は整数列と見なされます。

# 参照

[`combine`](@ref)、[`select`](@ref)、[`select!`](@ref)、[`transform`](@ref)、[`transform!`](@ref)

# 例

```jldoctest
julia> df = DataFrame(a=repeat([1, 2, 3, 4], outer=[2]),
                      b=repeat([2, 1], outer=[4]),
                      c=1:8);

julia> gd = groupby(df, :a)
GroupedDataFrame with 4 groups based on key: a
First Group (2 rows): a = 1
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     1      2      5
⋮
Last Group (2 rows): a = 4
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     4      1      4
   2 │     4      1      8

julia> gd[1]
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     1      2      5

julia> last(gd)
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     4      1      4
   2 │     4      1      8

julia> gd[(a=3,)]
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     3      2      3
   2 │     3      2      7

julia> gd[Dict("a" => 3)]
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     3      2      3
   2 │     3      2      7

julia> gd[(3,)]
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     3      2      3
   2 │     3      2      7

julia> k = first(keys(gd))
GroupKey: (a = 1,)

julia> gd[k]
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     1      2      5

julia> for g in gd
           println(g)
       end
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     1      2      5
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     2      1      2
   2 │     2      1      6
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     3      2      3
   2 │     3      2      7
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     4      1      4
   2 │     4      1      8
```
