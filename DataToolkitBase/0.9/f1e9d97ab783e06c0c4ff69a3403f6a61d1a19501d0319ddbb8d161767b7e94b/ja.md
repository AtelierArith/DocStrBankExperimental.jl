```
completions(r::ReplCmd, sofar::AbstractString)
```

`sofar`に基づいて`String`の補完候補のリストを取得します。すべての候補は`sofar`で始まる必要があります。

この関数が特定のReplCmd `r`に対して実装されていない場合、`allcompletions(r)`が呼び出され、`sofar`で始まる候補にフィルタリングされます。

`r`にサブコマンドがある場合、サブコマンドのプレフィックスは削除され、関連するサブコマンドに対して`completions`が再呼び出されます。
