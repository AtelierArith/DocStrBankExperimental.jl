```
dcc_send_data(src::AbstractString, filename; type = nothing)
dcc_send_data(writer::Function, data, filename; type = nothing)
```

文字列をダウンロードコンポーネントが期待する形式に変換します。`writer` 関数は `(io::IO, data)` のシグネチャを持つ必要があります。

# 例

文字列コンテンツの送信

```julia
text_data = "this is the test"
callback!(app, Output("download", "data"), Input("download-btn", "n_clicks"), prevent_initial_call = true) do n_clicks
    return dcc_send_string(text_data, "text.txt")
end
```

`CSV` 形式での `DataFrame` の送信

```julia
using DataFrames, CSV
...
df = DataFrame(...)
callback!(app, Output("download", "data"), Input("download-btn", "n_clicks"), prevent_initial_call = true) do n_clicks
    return dcc_send_string(CSV.write, df, "df.csv")
end
```
