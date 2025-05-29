```
block(b::Behavior)
block(b::Behavior, millis)
```

Marks a behavior as blocked, and prevents it from running until it is restarted using `restart(b)`. If `millis` is specified, the behavior is automatically restarted after `millis` milliseconds.
