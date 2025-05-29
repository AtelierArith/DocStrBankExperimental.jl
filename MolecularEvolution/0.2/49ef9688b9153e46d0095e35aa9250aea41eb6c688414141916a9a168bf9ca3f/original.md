```
refresh!(tree::FelNode, models; partition_list = 1:length(tree.message))
```

Run `felsenstein!` and `felsenstein_down!` on `tree` with `models` to refresh messages.
