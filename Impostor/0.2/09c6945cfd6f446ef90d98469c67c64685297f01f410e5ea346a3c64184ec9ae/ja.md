```
render_alphanumeric_range(template::AbstractString) :: String
```

数値範囲テンプレートから数値を含む文字列を生成します。このような数値テンプレートは、`';'` 文字で区切られたオプションを含む場合があります。さらに、オプションは単一のテンプレート形式（例: `"4##"`）を取ることも、オプション内で `':'` 文字を使用して範囲を指定することもできます（例: `"2##:3##"` は200から399の間の数値を指定します）。

# 例

```@repl
julia> render_alphanumeric_range("4#####")
"412345"

julia> render_alphanumeric_range("34####;37####")  # 34#### または 37#### を選択
"349790"

julia> render_alphanumeric_range("51####:55####")
"532489"

julia> render_alphanumeric_range("2221##:2720##;51####:55####")  # 2221##:2720## または 51####:55#### を選択
"250000"
```
