```
timespan_finish(ctx, category::Symbol, id, tl)
```

`Event{:finish}`を生成し、イベントの終了を示します。このイベントは`category`によって分類され、`id`によって一意に識別されます。これら2つは、以前に`timespan_start`に渡されたものと同じでなければなりません。`tl`はイベントの「タイムライン」であり、イベントに付随する任意のペイロードです。
