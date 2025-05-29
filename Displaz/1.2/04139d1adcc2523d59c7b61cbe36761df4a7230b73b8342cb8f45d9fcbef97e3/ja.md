```
event_loop(callback::Function, [plotobj::DisplazWindow], event_list...)
```

イベントのリストにサブスクライブし、イベントを受信するたびに `callback` を呼び出します。

各イベントには、イベントがトリガーされた時に付随するオプションの状態がいくつかあります。イベントは `event=>state` ペアのリストとして指定されます。

現在、サポートされているのは `KeyEvent` のみで、可能な引数は `Nothing` または `CursorPosition` です。例えば：

```
Displaz.event_loop(
        KeyEvent("c")=>Nothing,
        KeyEvent("p")=>CursorPosition
) do event, arg
    @show event, arg
    if event == KeyEvent("c")
        clearplot()
    end
end
```
