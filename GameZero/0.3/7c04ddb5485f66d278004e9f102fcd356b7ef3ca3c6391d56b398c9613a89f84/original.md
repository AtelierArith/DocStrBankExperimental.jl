```
schedule_interval(f::Function, interval, first_interval=interval)
```

Takes a function handle and time in seconds, and sets the function to run after that interval.  Optional third argument first_interval can be passed to wait for that amount of time before first execution.
