```
timespan_start(ctx, category::Symbol, id, tl)
```

`Event{:start}`を生成し、イベントの開始を示します。イベントは`category`によって分類され、`id`によって一意に識別されます。これら2つは、イベントを終了するために`timespan_finish`に渡されるものと同じでなければなりません。`tl`はイベントの「タイムライン」であり、イベントに添付された任意のペイロードです。
