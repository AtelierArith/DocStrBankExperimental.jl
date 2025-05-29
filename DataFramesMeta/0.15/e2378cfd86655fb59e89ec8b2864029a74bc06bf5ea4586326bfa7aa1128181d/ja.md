```
printlabels(df, [cols=All()]; unlabelled = true)
```

データフレーム内のすべてのラベルを整形して表示します。

## 引数

  * `cols`: 表示する列を選択するためのオプション引数。`Not(...)`、`Between(...)`、または正規表現など、任意の有効な複数列セレクタを指定できます。
  * `unlabelled`: ユーザー定義のラベルなしで列を表示するかどうかのキーワード引数。デフォルトは`true`です。ユーザー定義のラベルがない列`col`については、`label(df, col)`は列の名前`col`を返します。

## 例

```julia-repl
julia> df = DataFrame(wage = [12], age = [23]);

julia> @label! df :wage = "Hourly wage (2015 USD)";

julia> printlabels(df)
┌────────┬────────────────────────┐
│ Column │                  Label │
├────────┼────────────────────────┤
│   wage │ Hourly wage (2015 USD) │
│    age │                    age │
└────────┴────────────────────────┘

julia> printlabels(df, :wage)
┌────────┬────────────────────────┐
│ Column │                  Label │
├────────┼────────────────────────┤
│   wage │ Hourly wage (2015 USD) │
└────────┴────────────────────────┘

julia> printlabels(df; unlabelled = false)
┌────────┬────────────────────────┐
│ Column │                  Label │
├────────┼────────────────────────┤
│   wage │ Hourly wage (2015 USD) │
└────────┴────────────────────────┘

julia> printlabels(df, r"^wage")
┌────────┬────────────────────────┐
│ Column │                  Label │
├────────┼────────────────────────┤
│   wage │ Hourly wage (2015 USD) │
└────────┴────────────────────────┘
```
