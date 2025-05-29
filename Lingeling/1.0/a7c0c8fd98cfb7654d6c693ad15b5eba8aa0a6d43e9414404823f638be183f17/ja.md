```
LglPtr
```

Lingelingソルバーのラッパー。オブジェクトはLingeling Cライブラリによって完全に管理されていますが、メモリは`lgl_release`を使用して手動で解放する必要があります。

# フィールド

  * `ptr::Ptr{Cvoid}`: Lingelingソルバーへのポインタ。
