```
log_histogram(logger, name, data::Vector; step=step(logger))
```

`data` に見つかった値をビン分けし、タグ `name` の下でヒストグラムとしてログします。
