```
dcc_send_bytes(src::AbstractVector{UInt8}, filename; type = nothing)
dcc_send_bytes(writer::Function, data, filename; type = nothing)
```

バイトのベクターをダウンロードコンポーネントが期待する形式に変換します。`writer`関数は`(io::IO, data)`というシグネチャを持つ必要があります。

# 例

バイナリコンテンツの送信

```julia
file_data = read("path/to/file")
callback!(app, Output("download", "data"), Input("download-btn", "n_clicks"), prevent_initial_call = true) do n_clicks
    return dcc_send_bytes(file_data, "filename.fl")
end
```

`Arrow`形式での`DataFrame`の送信

```julia
using DataFrames, Arrow
...
df = DataFrame(...)
callback!(app, Output("download", "data"), Input("download-btn", "n_clicks"), prevent_initial_call = true) do n_clicks
    return dcc_send_bytes(Arrow.write, df, "df.arr")
end
```
