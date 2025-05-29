```
function pushsample!(::AbstractChain, sample...) -> AbstractChain
```

チェーンに新しいサンプルを追加します。これは `push!` ではなく、サンプルが複数の引数にまたがって表現される可能性があるためです。
