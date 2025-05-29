```
@by(d::AbstractDataFrame, cols, e...; kwargs...)
```

一歩で分割・適用・結合。

### 引数

  * `d` : AbstractDataFrame
  * `cols` : 列インジケーター (Symbol, Int, Vector{Symbol} など)
  * `e` : 列のグループ化に基づいて新しい列を指定する `:y = f(:x)` の形式のキーワードのような引数
  * `kwargs` : `DataFrames.combine` に渡されるキーワード引数

### 戻り値

  * `::DataFrame` または `GroupedDataFrame`

### 詳細

`@by` への変換入力は、`begin ... end` ブロックの形式と、キーワードのような引数の形式の2つで提供できます。この場合、ブロック内の各行は別々の変換です。例えば、以下は同等です：

```
@by df :g begin
    :mx = mean(:x)
    :sx = std(:x)
end
```

および

```
@by(df, :g, mx = mean(:x), sx = std(:x))
```

変換は、複数の新しい列を一度に作成し、変換が同じ名前空間を共有できるようにするために、マクロフラグ [`@astable`](@ref) を使用することもできます。詳細については `? @astable` を参照してください。

`@by` は `DataFrames.combine` と同じキーワード引数を受け入れ、2つの方法で追加できます。入力が複数の引数として与えられる場合、それらはセミコロン `;` の後に追加されます。例えば：

```
@by(ds, :g, :x = first(:a); ungroup = false)
```

入力が「ブロック」形式で与えられる場合、最後の行は `@kwarg key = value` と書くことができ、これは `combine` 関数に渡されるキーワード引数を示します。

```
@by df :a begin
    :x = first(:a)
    @kwarg ungroup = false
end
```

`@by` は `groupby` と `combine` の両方を実行しますが、`@by` はキーワード引数を `combine` にのみ転送し、`groupby` には転送しません。`groupby` にキーワード引数を渡すには、`groupby` と `@combine` のステップを別々に実行してください。

### 例

```julia
julia> using DataFramesMeta, Statistics

julia> df = DataFrame(
            a = repeat(1:4, outer = 2),
            b = repeat(2:-1:1, outer = 4),
            c = 1:8);

julia> @by(df, :a, :d = sum(:c))
4×2 DataFrame
 Row │ a      d
     │ Int64  Int64
─────┼──────────────
   1 │     1      6
   2 │     2      8
   3 │     3     10
   4 │     4     12

julia> @by df :a begin
           :d = 2 * :c
       end
8×2 DataFrame
 Row │ a      d
     │ Int64  Int64
─────┼──────────────
   1 │     1      2
   2 │     1     10
   3 │     2      4
   4 │     2     12
   5 │     3      6
   6 │     3     14
   7 │     4      8
   8 │     4     16

julia> @by(df, :a, :c_sum = sum(:c), :c_mean = mean(:c))
4×3 DataFrame
 Row │ a      c_sum  c_mean
     │ Int64  Int64  Float64
─────┼───────────────────────
   1 │     1      6      3.0
   2 │     2      8      4.0
   3 │     3     10      5.0
   4 │     4     12      6.0

julia> @by df :a begin
           :c = :c
           :c_mean = mean(:c)
       end
8×3 DataFrame
 Row │ a      c      c_mean
     │ Int64  Int64  Float64
─────┼───────────────────────
   1 │     1      1      3.0
   2 │     1      5      3.0
   3 │     2      2      4.0
   4 │     2      6      4.0
   5 │     3      3      5.0
   6 │     3      7      5.0
   7 │     4      4      6.0
   8 │     4      8      6.0

```
