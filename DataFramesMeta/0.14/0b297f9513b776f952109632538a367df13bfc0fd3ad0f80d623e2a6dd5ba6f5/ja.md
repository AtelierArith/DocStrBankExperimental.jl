```
@combine(x, args...; kwargs...)
```

グループ化操作の要約

### 引数

  * `x` : `GroupedDataFrame` または `AbstractDataFrame`
  * `args...` : 新しい列を定義する変換、形式は `:y = f(:x)`
  * `kwargs` : `DataFrames.combine` に渡されるキーワード引数

### 結果

  * `DataFrame` または `GroupedDataFrame`

### 詳細

`@combine` への入力は、`begin ... end` ブロックの形式と、キーワードのような引数の系列の形式の2つで提供できます。例えば、以下は同等です：

```
@combine df begin
    :mx = mean(:x)
    :sx = std(:x)
end
```

および

```
@combine(df, :mx = mean(:x), :sx = std(:x))
```

変換は、複数の新しい列を一度に作成し、変換が同じ名前空間を共有できるようにするためにマクロフラグ [`@astable`](@ref) を使用することもできます。詳細については `? @astable` を参照してください。

`@combine` は `DataFrames.combine` と同じキーワード引数を受け入れ、2つの方法で追加できます。入力が複数の引数として与えられる場合、それらはセミコロン `;` の後に追加されます。例えば：

```
@combine(gd, :x = first(:a); ungroup = false)
```

入力が「ブロック」形式で与えられる場合、最後の行は `@kwarg key = value` と書くことができ、これは `combine` 関数に渡されるキーワード引数を示します。

```
@combine gd begin
    :x = first(:a)
    @kwarg ungroup = false
end
```

### 例

```julia
julia> using DataFramesMeta

julia> d = DataFrame(
            n = 1:20,
            x = [3, 3, 3, 3, 1, 1, 1, 2, 1, 1, 2, 1, 1, 2, 2, 2, 3, 1, 1, 2]);

julia> g = groupby(d, :x);

julia> @combine(g, :nsum = sum(:n))
3×2 DataFrame
 Row │ x      nsum
     │ Int64  Int64
─────┼──────────────
   1 │     1     99
   2 │     2     84
   3 │     3     27

julia> @combine g begin
           :x2 = 2 * :x
           :nsum = sum(:n)
       end
20×3 DataFrame
 Row │ x      x2     nsum
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2     99
   2 │     1      2     99
   3 │     1      2     99
   4 │     1      2     99
   5 │     1      2     99
   6 │     1      2     99
   7 │     1      2     99
   8 │     1      2     99
   9 │     1      2     99
  10 │     2      4     84
  11 │     2      4     84
  12 │     2      4     84
  13 │     2      4     84
  14 │     2      4     84
  15 │     2      4     84
  16 │     3      6     27
  17 │     3      6     27
  18 │     3      6     27
  19 │     3      6     27
  20 │     3      6     27

```
