```
reversemap(f, args)
```

は、引数 `args` に対して関数 `f` を逆順で適用し、結果を返します。現時点では、引数 `args` は単純なタプルの形でなければならず、結果はタプル `(f(args[end]),f(args[end-1]),...,f(args[1]))` です。

また、`map`、`ntuple` も参照してください。
