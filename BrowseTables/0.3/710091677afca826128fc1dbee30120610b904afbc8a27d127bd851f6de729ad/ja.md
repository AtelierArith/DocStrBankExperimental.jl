```julia
write_html_table(io, table; title, caption, options)

```

`table`のHTML表現を`io`に書き込みます。`io`の代わりにファイルパス（文字列）を指定することもできます。

`title`と`caption`はそれぞれテーブルの部分を決定します。これらはエスケープされます。

`options`は、CSSなどのテーブルオプションを指定するために使用できます。
