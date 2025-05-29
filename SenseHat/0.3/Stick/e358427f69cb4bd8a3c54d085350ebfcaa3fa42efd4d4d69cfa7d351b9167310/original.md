```
sticktask()
```

This is a `Task` that produces `StickEvent`s when the joystick on the Sense HAT is manipulated. It will block until new `StickEvent`s occur. A typical usage will be to create a new task which will call this asynchronously, e.g. the following will call the function `f(::StickEvent)` for each event:

```
@schedule for e in sticktask()
    f(e)
end
```
