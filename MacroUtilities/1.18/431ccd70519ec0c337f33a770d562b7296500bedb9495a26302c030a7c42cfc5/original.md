```
map_kwargs(f, expr::FuncCall) -> FuncCall
map_kwargs(f, expr::FuncDef) -> FuncCall
```

Transform the `expr` by applying `f(FuncArg) -> FuncArg` to each of its keyword arguments
