```
allcompletions(r::ReplCmd)
```

`r`のすべての可能な`String`補完候補を取得します。これはデフォルトで空のベクター`String[]`になります。

`allcompletions`は、`completions(r, sofar::AbstractString)`が実装されていない場合にのみ呼び出されます。
