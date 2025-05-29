```
setdata!(buf::FastReadBuffer, data::AbstractVector{UInt8))
```

`data`のデータを`buf`の内部データバッファにコピーし、位置を先頭にリセットします。
