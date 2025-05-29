```
timeouts(handle::FT_HANDLE, timeout_rd, timeout_wr)
```

オープンされた [`FT_HANDLE`](@ref) のタイムアウトを [`FT_SetTimeouts`](@ref) を使用して設定します。

`timeout_rd` = 0 および `timeout_wr` = 0 の場合、動作は未定義です。 `timeout_rd` = 0 は [`read`](@ref) および [`readavailable`](@ref) がブロックされる原因となるようです。

関連情報: [`isopen`](@ref), [`open`](@ref)
