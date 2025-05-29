レクサー入力で引用符で囲まれた文字列を通過して位置を進めます。これは、`lexeme(lexer)`が引用符で囲まれた文字列を返すことを意味します。例：

```
if scan_string(l)
    emit_token(l, STRING)
end
```
