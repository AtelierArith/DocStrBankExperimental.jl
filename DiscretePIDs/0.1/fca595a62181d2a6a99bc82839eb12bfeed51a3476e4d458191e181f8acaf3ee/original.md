```
u = calculate_control!(pid::DiscretePID, r, y, uff=0)
(pid)(r, y, uff=0) # Alternative syntax
```

Calculate the control output from the PID controller when `r` is the reference (set point), `y` is the latest measurement and `uff` is the feed-forward contribution. If the type of the input arguments differ from the numeric type used by the PID controller, they will be converted before computations are performed.
