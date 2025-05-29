```
event_loop(callback::Function, [plotobj::DisplazWindow], event_list...)
```

Subscribe to a list of events, calling `callback` each time one is received.

Each event comes with some optional some state which is attached at the time the event is triggered.  The events are specified as a list of `event=>state` pairs.

Currently only `KeyEvent` is supported, with the possible arguments `Nothing` or `CursorPosition`.  For example:

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
