```
@label!(df, args...)
```

データフレームの列に `:col = label` 構文を使用してラベルを割り当てます。TablesMetaDataTools.jlの `label!(df, ...)` の短縮形です。

```julia-repl
julia> df = DataFrame(wage = 12);

julia> @label! df :wage = "Wage per hour (USD)";

julia> printlabels(df)
┌────────┬─────────────────────┐
│ Column │               Label │
├────────┼─────────────────────┤
│   wage │ Wage per hour (USD) │
└────────┴─────────────────────┘
```

短い説明には `@label!` を使用し、主に見栄えを良くするために使用します。列の長い説明には `@note!` を使用します。

ラベルは「ノート」スタイルの列メタデータです。ラベルは名前変更や変換時に保持されます。 `@label! :x = "Lab"` は列 `:x` の既存のラベルを上書きします。上書きせずに情報を追加するには、[`@note!`](@ref) を使用します。

`df` を返し、`df` のラベルが変更されます。

他のDataFramesMeta.jlマクロと同様に、`@label!` は「キーワード」形式とブロック形式の両方で使用できます。

```julia-repl
julia> df = DataFrame(wage = 12, tenure = 4);

julia> @label! df begin
           :wage = "Wage per hour (USD)"
           :tenure = "Tenure at job (months)"
       end;

julia> printlabels(df)
┌────────┬────────────────────────┐
│ Column │                  Label │
├────────┼────────────────────────┤
│   wage │    Wage per hour (USD) │
│ tenure │ Tenure at job (months) │
└────────┴────────────────────────┘
```
