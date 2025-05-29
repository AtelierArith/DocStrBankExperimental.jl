Advancing the position in the lexer input passed any quoted string. It means `lexeme(lexer)` will return a quoted string. Example:

```
if scan_string(l)
    emit_token(l, STRING)
end
```
