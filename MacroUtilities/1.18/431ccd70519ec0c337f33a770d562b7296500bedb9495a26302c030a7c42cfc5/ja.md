```
map_kwargs(f, expr::FuncCall) -> FuncCall
map_kwargs(f, expr::FuncDef) -> FuncCall
```

`expr`を変換し、各キーワード引数に`f(FuncArg) -> FuncArg`を適用します。
