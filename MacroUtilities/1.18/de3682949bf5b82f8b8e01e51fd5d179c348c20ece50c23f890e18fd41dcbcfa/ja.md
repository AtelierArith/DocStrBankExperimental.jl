```
map_args(f, expr::FuncCall) -> FuncCall
map_args(f, expr::FuncDef) -> FuncCall
```

`expr`を変換し、各引数に`f(FuncArg) -> FuncArg`を適用します。
