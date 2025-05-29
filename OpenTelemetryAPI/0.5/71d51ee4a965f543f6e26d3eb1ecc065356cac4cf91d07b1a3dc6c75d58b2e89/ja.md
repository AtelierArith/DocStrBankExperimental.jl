```
span_status!([current_span()], code::SpanStatusCode, description=nothing)
```

スパン`s`のステータスを元の仕様に従って更新します。`description`は`code`が`SPAN_STATUS_ERROR`のときのみ考慮されます。スパンがまだ終了していない場合にのみ有効です。
