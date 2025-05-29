```
@select(d, i...; kwargs...)
```

列を選択して変換します。

### 引数

  * `d` : `AbstractDataFrame` または `GroupedDataFrame`
  * `i` : 既存の列またはシンボルを指定して新しい列を定義する形の変換 `:y = f(:x)`
  * `kwargs` : `DataFrames.select` に渡されるキーワード引数

### 戻り値

  * `::AbstractDataFrame` または `GroupedDataFrame`

### 詳細

`@select` の入力は、2つの形式で提供できます。1つは `begin ... end` ブロックで、ブロック内の各行が別々の変換またはセレクタになります。もう1つは、引数とキーワードのような引数のシリーズです。例えば、以下は同等です：

```julia
@select df begin
    :x
    :y = :a .+ :b
end
```

と

```
@select(df, :x, :y = :a .+ :b)
```

`@select` は、`ByRow` 関数ラッパーを使って変換をラップするために `@byrow` 構文を使用し、ブロードキャスティングに似た形で行ごとに関数を適用します。例えば、次の呼び出しは

```
@select(df, @byrow :y = :x == 1 ? true : false)
```

となり、

```
select(df, :x => ByRow(x -> x == 1 ? true : false) => :y)
```

という変換になります。これはブロードキャスティングを使って便利に表現できないものです。

行ごとに複数の変換を行う際に `@byrow` を何度も書かなくて済むように、`@select` では選択のブロックの最初に `@byrow` を置くことができます（つまり `@byrow begin... end`）。ブロック内のすべての変換は行ごとに操作されます。

複数の列を一度に選択するには、`Not`、`Between`、`All`、および `Cols` のツールを使用します。

  * `@select df Not(:a)` は `:a` を除くすべての列を保持します
  * `@select df Between(:a, :z)` は `:a` から `:z` までのすべての列を保持します（両端を含む）
  * `@select df All()` はすべての列を保持します
  * `@select df Cols(...)` は多くの異なるセレクタを組み合わせたり、正規表現を使用したりするために使用できます。例えば `Cols(r"a")` は `"a"` で始まるすべての列を選択します。

`Not(...)`、`Between(...)` などの内部の式は、DataFramesMeta のパースによって変更されません。`Not` 内で列を表す変数 `x` を参照するには、`Not(x)` と書き、`Not($x)` とは書かないでください。

変換は、複数の新しい列を一度に作成し、変換が同じ名前空間を共有できるようにするためにマクロフラグ [`@astable`](@ref) を使用することもできます。詳細については `? @astable` を参照してください。

操作では、`AsTable(cols)` を使用して複数の列を一度に操作することも許可されています。ここで、列は `NamedTuple` にまとめられます。操作内で `AsTable(cols)` が現れると、ブロック内で他の列を参照することはできません。

この方法で `AsTable` を使用することは、プログラム的に多くの列を一度に操作するのに便利です。例えば、列 `[:a, :b, :c, :d]` の行ごとの合計を計算するには、次のように書きます。

```
@byrow :c = sum(AsTable([:a, :b, :c, :d]))
```

これにより、次のペアが構築されます。

```
AsTable(nms) => ByRow(sum) => :c
```

右辺の `AsTable` も、特別な列セレクタ `Not`、`Between`、および正規表現の使用を許可します。例えば、文字 `"a"` で始まるすべての列の積を計算するには、次のように書きます。

```
@byrow :d = prod(AsTable(r"^a"))
```

`@select` は `DataFrames.select` と同じキーワード引数を受け入れ、2つの方法で追加できます。入力が複数の引数として与えられる場合、それらはセミコロン `;` の後に追加されます。例えば、

```
@select(df, :a; copycols = false)
```

入力が「ブロック」形式で与えられる場合、最後の行は `@kwarg key = value` と書くことができ、これは `select` 関数に渡されるキーワード引数を示します。

```
@select gd begin
    :a
    @kwarg copycols = false
end
```

### 例

```jldoctest
julia> using DataFramesMeta

julia> df = DataFrame(a = repeat(1:4, outer = 2), b = repeat(2:-1:1, outer = 4), c = 1:8);

julia> @select(df, :c, :a)
8×2 DataFrame
 Row │ c      a
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3
   4 │     4      4
   5 │     5      1
   6 │     6      2
   7 │     7      3
   8 │     8      4

julia> @select df begin
           :c
           :x = :b + :c
       end
8×2 DataFrame
 Row │ c      x
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      3
   3 │     3      5
   4 │     4      5
   5 │     5      7
   6 │     6      7
   7 │     7      9
   8 │     8      9
```
