```
@select!(d, i...; kwargs...)
```

`d`をインプレースで変更して、`e`で指定された列または変換のみを保持し、それを返します。既存の列のコピーは作成されません。

### 引数

  * `d` : AbstractDataFrame
  * `i` : 既存の列またはシンボルを指定する形の変換 `:y = f(:x)`

新しい列を既存の列に基づいて指定します。

  * `kwargs` : `DataFrames.select!`に渡されるキーワード引数

### 戻り値

  * `::DataFrame`

### 詳細

`@select!`への入力は2つの形式で行うことができます：`begin ... end`ブロックの場合、ブロック内の各行は別々の変換またはセレクタであり、または一連の引数とキーワードのような引数として。例えば、以下は同等です：

`@select!`は、変換を`ByRow`関数ラッパーでラップするために`@byrow`構文を使用し、ブロードキャスティングに似て、行単位で関数を適用します。例えば、次の呼び出しは

```
@select!(df, @byrow :y = :x == 1 ? true : false)
```

次のようになります：

```
select!(df, :x => ByRow(x -> x == 1 ? true : false) => :y)
```

ブロードキャスティングを使用して便利に表現できない変換です。

行ごとに複数の変換を行う際に`@byrow`を何度も書くのを避けるために、`@select!`は`select!`の選択ブロックの最初に`@byrow`を許可します（つまり、`@byrow begin... end`）。ブロック内のすべての変換は行単位で操作されます。

複数の列を一度に選択するには、`Not`、`Between`、`All`、および`Cols`のツールを使用します。

  * `@select df Not(:a)`は`:a`を除くすべての列を保持します。
  * `@select df Between(:a, :z)`は`:a`と`:z`の間のすべての列を保持します（両端を含む）。
  * `@select df All()`はすべての列を保持します。
  * `@select df Cols(...)`は、さまざまなセレクタを組み合わせたり、正規表現を使用したりするために使用できます。例えば、`Cols(r"a")`は、`"a"`で始まるすべての列を選択します。

変換は、複数の新しい列を一度に作成し、変換が同じ名前空間を共有できるようにするためにマクロフラグ[`@astable`](@ref)を使用することもできます。詳細については、`? @astable`を参照してください。

操作では、`AsTable(cols)`を使用して複数の列を一度に操作することも許可されており、列は`NamedTuple`にグループ化されます。操作内で`AsTable(cols)`が出現する場合、ブロック内で他の列を参照することはできません。

この方法で`AsTable`を使用することは、プログラム的に多くの列を一度に操作するのに便利です。例えば、列`[:a, :b, :c, :d]`の行ごとの合計を計算するには、次のように書きます。

```
@byrow :c = sum(AsTable([:a, :b, :c, :d]))
```

これにより、次のペアが構築されます。

```
AsTable(nms) => ByRow(sum) => :c
```

右辺の`AsTable`は、特別な列セレクタ`Not`、`Between`、および正規表現の使用も許可します。例えば、文字`"a"`で始まるすべての列の積を計算するには、次のように書きます。

```
@byrow :d = prod(AsTable(r"^a"))
```

`@select!`は`DataFrames.select!`と同じキーワード引数を受け入れ、2つの方法で追加できます。入力が複数の引数として与えられる場合、それらはセミコロン`;`の後に追加されます。例えば、

```
@select!(gd, :a; ungroup = false)
```

入力が「ブロック」形式で与えられる場合、最後の行は`@kwarg key = value`と書くことができ、これは`select!`関数に渡されるキーワード引数を示します。

```
@select! gd begin
    :a
    @kwarg ungroup = false
end
```

### 例

```jldoctest
julia> using DataFrames, DataFramesMeta

julia> df = DataFrame(a = repeat(1:4, outer = 2), b = repeat(2:-1:1, outer = 4), c = 1:8);

julia> df2 = @select!(df, :c, :a)
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

julia> df === df2
true

julia> df = DataFrame(a = repeat(1:4, outer = 2), b = repeat(2:-1:1, outer = 4), c = 1:8);

julia> df2 = @select! df begin
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

julia> df === df2
true
```
