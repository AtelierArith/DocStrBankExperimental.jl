```
@linq df ...
```

!!! note
    `@linq` は非推奨です。代わりに `@chain` を使用してください。詳細は `? @chain` を参照してください。


一般的なマクロで、チェーンおよびマクロ呼び出しのためのミニDSLを作成します。

### 詳細

以下の埋め込み関数呼び出しは、それぞれのマクロバージョンと同等です：

  * `with`
  * `where`
  * `select`
  * `transform`
  * `by`
  * `groupby`
  * `orderby`
  * `combine`

### 例

```julia
julia> using DataFramesMeta, Statistics

julia> df = DataFrame(
            a = repeat(1:4, outer = 2),
            b = repeat(2:-1:1, outer = 4),
            x = 1:8);

julia> x1 = @linq transform(where(df, :a .> 2, :b .!= "c"), :y = 10 .* :x);

julia> x1 = @linq by(x1, :b, :meanX = mean(:x), :meanY = mean(:y));

julia> @linq select(orderby(x1, :b, -:meanX), :var = :b, :meanX, :meanY)
2×3 DataFrame
│ Row │ var   │ meanX   │ meanY   │
│     │ Int64 │ Float64 │ Float64 │
├─────┼───────┼─────────┼─────────┤
│ 1   │ 1     │ 6.0     │ 60.0    │
│ 2   │ 2     │ 5.0     │ 50.0    │

julia> @linq df |>
           transform(y = 10 .* :x) |>
           where(:a .> 2) |>
           by(:b, :meanX = mean(:x), :meanY = mean(:y)) |>
           orderby(:meanX) |>
           select(:meanX, :meanY, var = :b)
2×3 DataFrame
│ Row │ meanX   │ meanY   │ var   │
│     │ Float64 │ Float64 │ Int64 │
├─────┼─────────┼─────────┼───────┤
│ 1   │ 5.0     │ 50.0    │ 2     │
│ 2   │ 6.0     │ 60.0    │ 1     │

```
