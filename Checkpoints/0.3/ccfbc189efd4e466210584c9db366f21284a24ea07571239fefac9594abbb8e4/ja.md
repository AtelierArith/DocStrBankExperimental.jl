```
checkpoint([prefix], name, data)
checkpoint([prefix], name, data::Pair...)
checkpoint([prefix], name, data::Dict)
```

指定された `label` と値 `data` でデータチェックポイントを定義します。デフォルトでは、チェックポイントは何もしない操作であり、明示的に設定する必要があります。

```
checkpoint(session, data)
checkpoint(handler, name, data::Dict)
```

また、セッションにチェックポイントを設定することもでき、これは後で `commit!(session)` によってコミットされるデータをステージングします。ハンドラーでチェックポイントを明示的に呼び出すことは一般的には推奨されませんが、オプションとして利用可能です。
