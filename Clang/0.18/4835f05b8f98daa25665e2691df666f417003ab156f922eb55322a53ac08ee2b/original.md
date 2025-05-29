```
kind(c::CLCursor) -> CXCursorKind
```

Return the kind of the given cursor. Note this method directly reads CXCursor's `kind` field, which won't invoke additional `clang_getCursorKind` function calls.
