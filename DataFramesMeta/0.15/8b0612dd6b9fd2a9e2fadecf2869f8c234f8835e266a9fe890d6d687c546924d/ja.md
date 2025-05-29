```
@orderby(d, i...)
```

複数の列のいずれかの値または列の変換によって行をソートします。常に新しい `DataFrame` を返します。`GroupedDataFrame` は受け付けません。

### 引数

  * `d`: `DataFrame` または `GroupedDataFrame`
  * `i...`: オブジェクトをソートするための引数

### 詳細

`DataFrame` が与えられた場合、`@orderby` はその引数によって与えられた変換を適用し（新しい列は作成しません）、結果に基づいて与えられた `DataFrame` をソートし、新しい `DataFrame` を返します。

`@orderby` への入力は、2つの形式で提供できます。1つは `begin ... end` ブロックで、この場合、ブロック内の各行は別々の順序付け操作です。もう1つは複数の引数です。たとえば、次の2つの文は同等です。

```julia
@orderby df begin
    :x
    -:y
end
```

および

```
@orderby(df, :x, -:y)
```

### 引数

  * `d` : AbstractDataFrame
  * `i...` : ソートのための式

`@orderby` に提供された式が `@byrow` で始まる場合、操作はデータフレームに沿って「行ごと」に適用されます。`@byrow` を複数回書くのを避けるために、`@orderby` は操作のブロックの先頭に `@byrow` を置くことも許可します。たとえば、次の2つの文は同等です。

```
@orderby df @byrow begin
    :x^2
    :x^3
end
```

および

```
@orderby df
    @byrow :x^2
    @byrow :x^3
end
```

操作では、`AsTable(cols)` を使用して複数の列を一度に操作することも許可されており、列は `NamedTuple` にまとめられます。操作内で `AsTable(cols)` が現れると、ブロック内で他の列を参照することはできません。

このように `AsTable` を使用することは、プログラム的に多くの列を一度に操作するのに便利です。たとえば、列 `:a`、`:b`、および `:c` の合計で行を順序付けるには、次のように書きます。

```
@byrow sum(AsTable([:a, :b, :c]))
```

これにより、ペアが構築されます。

```
AsTable([:a, :b, :c]) => ByRow(sum)
```

右辺の `AsTable` では、特別な列セレクタ `Not`、`Between`、および正規表現を使用することもできます。たとえば、すべての列のうち `"a"` で始まるすべての列の積で行を順序付けるには、次のように書きます。

```
@byrow prod(AsTable(r"^a"))
```

### 例

```jldoctest
julia> using DataFramesMeta, Statistics

julia> d = DataFrame(x = [3, 3, 3, 2, 1, 1, 1, 2, 1, 1], n = 1:10,
                     c = ["a", "c", "b", "e", "d", "g", "f", "i", "j", "h"]);

julia> @orderby(d, -:n)
10×3 DataFrame
 Row │ x      n      c
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     1     10  h
   2 │     1      9  j
   3 │     2      8  i
   4 │     1      7  f
   5 │     1      6  g
   6 │     1      5  d
   7 │     2      4  e
   8 │     3      3  b
   9 │     3      2  c
  10 │     3      1  a

julia> @orderby(d, invperm(sortperm(:c, rev = true)))
10×3 DataFrame
 Row │ x      n      c
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     1      9  j
   2 │     2      8  i
   3 │     1     10  h
   4 │     1      6  g
   5 │     1      7  f
   6 │     2      4  e
   7 │     1      5  d
   8 │     3      2  c
   9 │     3      3  b
  10 │     3      1  a

julia> @orderby d begin
           :x
           abs.(:n .- mean(:n))
       end
10×3 DataFrame
 Row │ x      n      c
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     1      5  e
   2 │     1      6  f
   3 │     1      7  g
   4 │     1      9  i
   5 │     1     10  j
   6 │     2      4  d
   7 │     2      8  h
   8 │     3      3  c
   9 │     3      2  b
  10 │     3      1  a

julia> @orderby d @byrow :x^2
10×3 DataFrame
 Row │ x      n      c
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     1      5  e
   2 │     1      6  f
   3 │     1      7  g
   4 │     1      9  i
   5 │     1     10  j
   6 │     2      4  d
   7 │     2      8  h
   8 │     3      1  a
   9 │     3      2  b
  10 │     3      3  c
```
