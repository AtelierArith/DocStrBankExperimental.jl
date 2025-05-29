```
@transform(d, i...; kwargs...)
```

キーワードのような引数に基づいて追加の列またはキーを追加します。

### 引数

  * `d`: `AbstractDataFrame` または `GroupedDataFrame`
  * `i...`: 新しい列またはキーを定義する変換、形式は `:y = f(:x)`
  * `kwargs...`: `DataFrames.transform` に渡されるキーワード引数

### 戻り値

  * `::AbstractDataFrame` または `::GroupedDataFrame`

### 詳細

`@transform` の入力は、2つの形式で提供できます。1つは `begin ... end` ブロックで、ブロック内の各行が別々の変換（`:y = f(:x)`）になります。もう1つは、一連のキーワードのような引数です。例えば、以下は同等です：

```julia
@transform df begin
    :a = :x
    :b = :y
end
```

および

```
@transform(df, :a = :x, :b = :y)
```

`@transform` は、変換を `ByRow` 関数ラッパーでラップするために `@byrow` 構文を使用し、ブロードキャスティングに似て、行単位で関数を適用します。例えば、次の呼び出しは

```
@transform(df, @byrow :y = :x == 1 ? true : false)
```

次のようになります：

```
transform(df, :x => ByRow(x -> x == 1 ? true : false) => :y)
```

これは、ブロードキャスティングを使用して便利に表現できない変換です。

複数の行単位の変換を行う際に `@byrow` を何度も書くのを避けるために、`@transform` は変換のブロックの最初に `@byrow` を許可します（つまり、`@byrow begin... end`）。ブロック内のすべての変換は行単位で操作されます。

変換はまた、複数の新しい列を一度に作成し、変換が同じ名前空間を共有できるようにするためにマクロフラグ [`@astable`](@ref) を使用することもできます。詳細については `? @astable` を参照してください。

操作では、`AsTable(cols)` を使用して複数の列を一度に操作することも許可されており、列は `NamedTuple` にまとめられます。操作内で `AsTable(cols)` が現れると、ブロック内で他の列を参照することはできません。

このように `AsTable` を使用することは、プログラム的に多くの列を一度に操作するのに便利です。例えば、列 `[:a, :b, :c, :d]` の行単位の合計を計算するには、次のように書きます：

```
@byrow :c = sum(AsTable([:a, :b, :c, :d]))
```

これにより、次のペアが構築されます：

```
AsTable(nms) => ByRow(sum) => :c
```

右辺の `AsTable` は、特別な列セレクタ `Not`、`Between`、および正規表現の使用も許可します。例えば、文字 `"a"` で始まるすべての列の積を計算するには、次のように書きます：

```
@byrow :d = prod(AsTable(r"^a"))
```

`@transform` は `DataFrames.transform!` と同じキーワード引数を受け入れ、2つの方法で追加できます。入力が複数の引数として与えられると、それらはセミコロン `;` の後に追加されます。例えば：

```
@transform(gd, :x = :a .- 1; ungroup = false)
```

入力が「ブロック」形式で与えられると、最後の行は `@kwarg key = value` と書くことができ、これは `transform!` 関数に渡されるキーワード引数を示します。

```
@transform gd begin
    :x = :a .- 1
    @kwarg ungroup = false
end
```

### 例

```jldoctest
julia> using DataFramesMeta

julia> df = DataFrame(A = 1:3, B = [2, 1, 2]);

julia> @transform df begin
           :a = 2 * :A
           :x = :A .+ :B
       end
3×4 DataFrame
 Row │ A      B      a      x
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1      2      2      3
   2 │     2      1      4      3
   3 │     3      2      6      5

julia> @transform df @byrow :z = :A * :B
3×3 DataFrame
 Row │ A      B      z
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      2
   2 │     2      1      2
   3 │     3      2      6

julia> @transform df @byrow begin
           :x = :A * :B
           :y = :A == 1 ? 100 : 200
       end
3×4 DataFrame
 Row │ A      B      x      y
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1      2      2    100
   2 │     2      1      2    200
   3 │     3      2      6    200
```
