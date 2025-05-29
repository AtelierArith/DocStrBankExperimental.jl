```
function kfold(f, df, k, r = 1, shuffle=true; kwargs...)

単純な `k` フォールド交差検証を `r` 回繰り返します。
`kwargs` 引数は `regress` 関数呼び出しに渡されます。
この機能は部分的に PRESS 統計と重複しています。
```
