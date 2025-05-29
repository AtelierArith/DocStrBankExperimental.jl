```
function jlgetch(win::Union{Ptr{WINDOW},Nothing} = nothing)
```

ウィンドウ `win` でキー入力を待ち、その入力を返します（`Keystroke` を参照）。`win` が `nothing` の場合、`wgetch(win)` の代わりに `getch()` がキー入力を待つために使用されます。
