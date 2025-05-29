```
BijectiveSimplexLink(link)
```

リンク `link` に渡す前に、入力の最後に `0` を追加するためのラッパーです。これは単体と作業するために必要なステップです。たとえば、[`SoftMaxLink`](@ref) を使用して、[`CategoricalLikelihood`](@ref) のために `n`-単体を得るには、`n+1` のカテゴリが必要です。そのためには、`n+1` の潜在 GP を渡す必要があります。しかし、リンクを `BijectiveSimplexLink` でラップすることで、必要なのは `n` の潜在だけです。
