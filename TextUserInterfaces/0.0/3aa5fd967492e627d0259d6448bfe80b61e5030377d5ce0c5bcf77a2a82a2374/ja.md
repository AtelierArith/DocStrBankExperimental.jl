```
function refresh_window(win::Window; update = true, backpropagation = true)
```

ウィンドウ `win` とそのすべての子ウィンドウを更新します。ビューを更新する必要がある場合（`view_needs_update` を参照）、バッファの内容が更新前にビューにコピーされます。

`update` が `true` の場合、`doupdate()` が呼び出され、物理画面が更新されます。

`backpropagation` が `true` の場合、すべての親ウィンドウ（ルートウィンドウを除く）も更新されます。
