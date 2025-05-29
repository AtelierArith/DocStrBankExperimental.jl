```
function move_view(win::Window, y::Integer, x::Integer; update::Bool = true)
```

ウィンドウ `win` のビューの原点を位置 `(y,x)` に移動します。このルーチンは、ビューがバッファの外に達することがないようにします。
