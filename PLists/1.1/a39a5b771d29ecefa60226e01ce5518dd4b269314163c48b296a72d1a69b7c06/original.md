Advancing the position in the lexer input passed any number. It means `lexeme(lexer)` will return a number. To emit a number token you can just write:

```
if scan_number(l)
    emit_token(l, NUMBER)
end
```

The reason for doing it this way, is that it retains flexibility in with which lexer state should be associated with lexing a number. Several kinds of lexer will need to lex a number. So we want reusable functions.
