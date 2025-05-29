```
update_recent!(actr, chunk)
```

Adds a new timestamp to chunk and removes oldest timestamp if length equals k. By default, current time is computed with `get_time`.

# Arguments

  * `actr`: an ACT-R model object
  * `chunk`: memory chunk object
