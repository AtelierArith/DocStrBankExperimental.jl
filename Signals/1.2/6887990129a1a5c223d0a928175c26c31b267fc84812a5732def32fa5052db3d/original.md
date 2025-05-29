```
s = fpswhen(switch::Signal, freq; duration = Inf)
```

A signal that updates 'freq' times a second to the current timestamp, for `duration` seconds if and only if the value of `switch` is `true`.
