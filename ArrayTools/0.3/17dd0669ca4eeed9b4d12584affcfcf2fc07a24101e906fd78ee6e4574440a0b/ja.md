```
noneof(f, args...) -> bool
```

は、述語 `f` がすべての引数 `args...` に対して `false` を返すかどうかをチェックします。一方、

```
noneof(args...) -> bool
```

は、すべての引数 `args...` が `false` であるかどうかをチェックします。

他にも `any`、[`allof`](@ref)、[`noneof`](@ref) を参照してください。
