```
fill_forward_event(ts::EventSeries, time)
```

入力された `EventSeries` における `time` に対する前の `Event` を返します。

```
fill_forward_event(ts::TaggedEventSeries, time)
```

入力された `TaggedEventSeries` の各タグに対する `time` に対する前の `Event` を持つ名前付きタプルを返します。

`time` が `EventSeries` / `TaggedEventSeries` の最初のタイムスタンプより前の場合、`nothing` が返されます。
