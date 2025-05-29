```
queue(table; sortby=:created_at)
```

保留中、実行中、または完了したすべての `Job` を返します。

`sortby` に対して許可される引数は `:created_by`、 `:created_at`、 `:started_at`、 `:stopped_at`、 `:spent`、 `:status`、および `:n` です。
