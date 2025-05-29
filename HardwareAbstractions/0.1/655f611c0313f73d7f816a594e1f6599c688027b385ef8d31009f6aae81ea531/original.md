```
@periodically(h, simulation::Bool, body)
```

Ensures that the body is run with an interval of `h >= 0.001` seconds. If `simulation == false`, no sleep is done
