```
alarm(dt::DateTime;
    action = () -> @info("TickTock: time's up"))
```

Run an alarm that fires at time `dt`, with the option of providing a function that executes when alarm fires.

# Examples

```
using Dates

dt = now() + Dates.Minute(1)

@async alarm(dt, action = () -> println("TickTock.jl: Ready!"))
```

```
@async alarm(now() + Dates.Minute(10) + Dates.Second(0), action = () -> run(`say "wake up, 10 minutes is up"`)) # macOS speech command
```
