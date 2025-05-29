```
refresh!(tree::FelNode, models; partition_list = 1:length(tree.message))
```

`felsenstein!` と `felsenstein_down!` を `tree` に対して `models` で実行してメッセージを更新します。
