```
@subset(d, i...; kwargs...)
```

`AbstractDataFrame`および`GroupedDataFrame`の行のサブセットを選択します。

### 引数

  * `d` : AbstractDataFrameまたはGroupedDataFrame
  * `i...` : 行を選択するための式
  * `kwargs...` : `DataFrames.subset`に渡されるキーワード引数

### 詳細

複数の`i`式は「AND」で結合されます。

`GroupedDataFrame`が与えられた場合、`@subset`はグループごとに変換を適用し、生成された値がすべて`true`である行を含む新しい`DataFrame`を返します。

`@subset`への入力は、`begin ... end`ブロックの形式または複数の引数の形式で提供できます。たとえば、次の2つの文は同等です。

```julia
@subset df begin
    :x .> 1
    :y .< 2
end
```

と

```
@subset(df, :x .> 1, :y .< 2)
```

!!! 注     `@subset`は、行をフィルタリングする際に`missing`値を`false`として扱います。`DataFrames.subset`や`missing`を含む他のブール演算とは異なり、`@subset`は`missing`値でエラーを出さず、`true`値のみを保持します。

`@subset`に提供された式が`@byrow`で始まる場合、操作はデータフレームに沿って「行ごと」に適用されます。`@byrow`を複数回書くのを避けるために、`@orderby`は操作のブロックの先頭に`@byrow`を置くことも許可します。たとえば、次の2つの文は同等です。

```
@subset df @byrow begin
    :x > 1
    :y < 2
end
```

と

```
@subset df
    @byrow :x > 1
    @byrow :y < 2
end
```

操作では、`AsTable(cols)`を使用して複数の列を一度に操作することも許可されており、列は`NamedTuple`にまとめられます。操作内に`AsTable(cols)`が現れると、ブロック内で他の列を参照することはできません。

このように`AsTable`を使用することは、プログラム的に多くの列を一度に操作するのに便利です。たとえば、列`:a`、`:b`、`:c`の合計が`5`を超える行を選択するには、次のように書きます。

```
@byrow sum(AsTable([:a, :b, :c])) > 5
```

これにより、ペアが構築されます。

```
AsTable([:a, :b, :c]) => ByRow(t -> sum(t) > 5)
```

右辺の`AsTable`は、特別な列セレクタ`Not`、`Between`、および正規表現の使用も許可します。たとえば、すべての列が`"a"`で始まる行の積が`5`を超える行をサブセットするには、次のように書きます。

```
@byrow prod(AsTable(r"^a")) > 5
```

`@subset`は`DataFrames.subset`と同じキーワード引数を受け入れ、2つの方法で追加できます。入力が複数の引数として与えられる場合、それらはセミコロン`;`の後に追加されます。

```
@subset(df, :a; skipmissing = false, view = true)
```

入力が「ブロック」形式で与えられる場合、最後の行は`@kwarg key = value`と書くことができ、これは`subset`関数に渡されるキーワード引数を示します。

```
@subset df begin
    :a .== 1
    @kwarg skipmissing = false
    @kwarg view = true
end
```

### 例

```jldoctest
julia> using DataFramesMeta, Statistics

julia> df = DataFrame(x = 1:3, y = [2, 1, 2]);

julia> globalvar = [2, 1, 0];

julia> @subset(df, :x .> 1)
2×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     2      1
   2 │     3      2

julia> @subset(df, :x .> globalvar)
2×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     2      1
   2 │     3      2

julia> @subset df begin
           :x .> globalvar
           :y .== 3
       end
0×2 DataFrame

julia> df = DataFrame(n = 1:20, x = [3, 3, 3, 3, 1, 1, 1, 2, 1, 1,
                                    2, 1, 1, 2, 2, 2, 3, 1, 1, 2]);

julia> g = groupby(df, :x);

julia> @subset(g, :n .> mean(:n))
8×2 DataFrame
 Row │ n      x
     │ Int64  Int64
─────┼──────────────
   1 │    12      1
   2 │    13      1
   3 │    15      2
   4 │    16      2
   5 │    17      3
   6 │    18      1
   7 │    19      1
   8 │    20      2

julia> @subset g begin
           :n .> mean(:n)
           :n .< 20
       end
7×2 DataFrame
 Row │ n      x
     │ Int64  Int64
─────┼──────────────
   1 │    12      1
   2 │    13      1
   3 │    15      2
   4 │    16      2
   5 │    17      3
   6 │    18      1
   7 │    19      1

julia> df = DataFrame(a = [1, 2, missing], b = ["x", "y", missing]);

julia> @subset(df, :a .== 1)
1×2 DataFrame
 Row │ a       b
     │ Int64?  String?
─────┼─────────────────
   1 │      1  x

julia> @subset(df, :a .< 3; view = true)
2×2 SubDataFrame
 Row │ a       b
     │ Int64?  String?
─────┼─────────────────
   1 │      1  x
   2 │      2  y

julia> @subset df begin
           :a .< 3
           @kwarg view = true
       end
2×2 SubDataFrame
 Row │ a       b
     │ Int64?  String?
─────┼─────────────────
   1 │      1  x
   2 │      2  y
```
