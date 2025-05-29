```
busywait(seconds)
```

Like Base.sleep() except maxes out the thread for a specified number of seconds. The minimum busywait time is 1 millisecond or input of `0.001`.
