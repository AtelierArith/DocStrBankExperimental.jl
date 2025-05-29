```
@transform!(d, i...; kwargs...)
```

`d`をインプレースで変更して、キーワードのような引数に基づいて追加の列やキーを追加し、それを返します。既存の列のコピーは作成されません。

### 引数

  * `d` : `AbstractDataFrame` または `GroupedDataFrame`
  * `i...` : 新しい列やキーを定義する形式 `:y = f(:x)` の変換
  * `kwargs...`: `DataFrames.transform!` に渡されるキーワード引数

### 戻り値

  * `::DataFrame` または `GroupedDataFrame`

### 詳細

`@transform!` への入力は、2つの形式で提供できます：`begin ... end` ブロックの場合、ブロック内の各行は別々の変換（`:y = f(:x)`）であり、または一連のキーワードのような引数として。例えば、以下は同等です：

```julia
@transform! df begin
    :a = :x
    :b = :y
end
```

および

```
@transform!(df, :a = :x, :b = :y)
```

`@transform!` は、`ByRow` 関数ラッパーからの変換をラップするために `@byrow` 構文を使用し、ブロードキャスティングに似て、行単位で関数を適用します。例えば、呼び出し

```
@transform!(df, @byrow :y = :x == 1 ? true : false)
```

は次のようになります：

```
transform!(df, :x => ByRow(x -> x == 1 ? true : false) => :y)
```

これは、ブロードキャスティングを使用して便利に表現できない変換です。

複数の行単位の変換を行う際に `@byrow` を何度も書くのを避けるために、`@transform!` は変換のブロックの最初に `@byrow` を許可します（すなわち、`@byrow begin... end`）。ブロック内のすべての変換は行単位で操作されます。

変換は、複数の新しい列を一度に作成し、変換が同じ名前空間を共有できるようにするために、マクロフラグ [`@astable`](@ref) を使用することもできます。詳細については `? @astable` を参照してください。

操作では、`AsTable(cols)` を使用して複数の列を一度に操作することも許可されており、列は `NamedTuple` にまとめられます。操作内で `AsTable(cols)` が現れると、ブロック内で他の列を参照することはできません。

このように `AsTable` を使用することは、プログラム的に多くの列を一度に操作するのに便利です。例えば、列 `[:a, :b, :c, :d]` の行単位の合計を計算するには、次のように書きます：

```
@byrow :c = sum(AsTable([:a, :b, :c, :d]))
```

これにより、ペアが構築されます：

```
AsTable(nms) => ByRow(sum) => :c
```

右辺の `AsTable` は、特別な列セレクタ `Not`、`Between`、および正規表現の使用も許可します。例えば、文字 `"a"` で始まるすべての列の積を計算するには、次のように書きます：

```
@byrow :d = prod(AsTable(r"^a"))
```

`@transform!` は `DataFrames.transform!` と同じキーワード引数を受け入れ、2つの方法で追加できます。入力が複数の引数として与えられると、それらはセミコロン `;` の後に追加されます。例えば：

```
@transform!(gd, :x = :a .- 1; ungroup = false)
```

入力が「ブロック」形式で与えられると、最後の行は `@kwarg key = value` と書くことができ、これは `transform!` 関数に渡されるキーワード引数を示します。

```
@transform! gd begin
    :x = :a .- 1
    @kwarg ungroup = false
end
```

### 例

```jldoctest
julia> using DataFramesMeta

julia> df = DataFrame(A = 1:3, B = [2, 1, 2]);

julia> df2 = @transform!(df, :a = 2 * :A, :x = :A .+ :B)
3×4 DataFrame
 Row │ A      B      a      x
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1      2      2      3
   2 │     2      1      4      3
   3 │     3      2      6      5

julia> df === df2
true
```
