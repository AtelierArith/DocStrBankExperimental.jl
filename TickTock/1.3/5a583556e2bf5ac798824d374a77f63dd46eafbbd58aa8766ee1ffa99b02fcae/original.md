```
alarm(hours, minutes, seconds;
    action = () -> @info("TickTock: time's up"))
```

Set an alarm, with the option of providing a anonymous function that executes when alarm fires.

!!! warning
    Use @async to avoid tying up your terminal!


```
@async alarm(0, 5, 0, action = ()-> println("TickTock.jl: 5 minutes is up!"))

@async alarm(0, 0, 5, action = () -> run(`say "Your Earl Grey is ready; sir"`), alarmname="tea's up") # uses macOS speech
```
