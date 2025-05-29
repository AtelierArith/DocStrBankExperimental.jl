```
TimeSpan(start, stop)
```

`TimeSpan(Nanosecond(start), Nanosecond(stop))`は、区間`[start, stop)`を表します。

もし`start == stop`の場合、`stop`に単一の`Nanosecond`が追加されます。なぜなら、`stop`は排他的上限であり、TimeSpanの操作は一般的にナノ秒精度までしかサポートしていないからです。

この型の利点は、例えば`Nanosecond(start):Nanosecond(1):Nanosecond(stop)`に対して、構造上`TimeSpans.start(x) < TimeSpans.stop(x)`を遵守することが保証されている点です。
