```
xcb_connect(display_name:: Union{AbstractString, Nothing} = nothing) -> XCBConnection
```

`display_name`でXサーバーに接続します。`display_name`が`nothing`の場合、XCBは`DISPLAY`環境変数を使用します。この関数は、エラーが発生した場合に[`XCBConnectionError`](@ref)をスローします。
