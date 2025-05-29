```
get_elaborated_cursor(ty::CLType) -> CLCursor
get_elaborated_cursor(ty::CXType) -> CXCursor
```

入力タイプによって参照される詳細化されたタイプのカーソルを返します。入力タイプはポインタ/配列である可能性があります。この関数は、入力タイプが詳細化されたタイプを参照していない場合、[`clang_getNullCursor`](@ref)を返します。
