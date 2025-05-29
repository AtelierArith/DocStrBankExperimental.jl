```
kind(c::CLCursor) -> CXCursorKind
```

与えられたカーソルの種類を返します。このメソッドは直接CXCursorの`kind`フィールドを読み取るため、追加の`clang_getCursorKind`関数呼び出しは行われません。
