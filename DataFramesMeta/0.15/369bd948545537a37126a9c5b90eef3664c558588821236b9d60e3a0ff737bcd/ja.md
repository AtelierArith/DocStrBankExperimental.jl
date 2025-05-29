```
printnotes(df, cols = All(); unnoted = false)
```

データフレームのノートとラベルを印刷します。

## 引数

  * `cols`: 印刷する列を選択するためのオプション引数。`Not(...)`、`Between(...)`、または正規表現など、任意の有効なマルチカラムセレクタを使用できます。
  * `unnoted`: ユーザー定義のノートやラベルなしで列を印刷するかどうかのキーワード引数。

印刷の目的のために、列ラベルはノートに加えて印刷されます。ただし、列ラベルは`note(df, col)`によって返されません。

```
julia> df = DataFrame(wage = [12], age = [23]);

julia> @label! df :age = "年齢 (歳)";

julia> @note! df :wage = "アメリカ合衆国コミュニティ調査から派生";

julia> @note! df :wage = "欠損値は0賃金として補完されました";

julia> @label! df :wage = "時給 (2015年USD)";

julia> printnotes(df)
列: wage
────────────
ラベル: 時給 (2015年USD)
アメリカ合衆国コミュニティ調査から派生
欠損値は0賃金として補完されました

列: age
───────────
ラベル: 年齢 (歳)
```
