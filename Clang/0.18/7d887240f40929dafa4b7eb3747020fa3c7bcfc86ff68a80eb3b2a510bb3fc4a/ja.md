```
search(cursors::Vector{CLCursor}, ismatch::Function) -> Vector{CLCursor}
```

述語に一致するCLCursorのベクターを返します。`ismatch`はCLCursor引数を受け取る関数です。
