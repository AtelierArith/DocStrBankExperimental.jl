```
@wait_while [maxtime=nothing] [timeout_error=false] cond
```

Wait while `cond` is true, using slowly increasing sleep times in between evaluating `cond`.

`cond` may be an arbitrary Julia expression.

If `maxtime` is given with an real value, will only wait for `maxtime` seconds, if the value is zero or negative will not wait at all.

If `timeout_error` is `true`, will throw a `TimelimitExceeded` exception if the maximum waiting time is exceeded.

Example, wait for a task with a maxtime:

```julia
task = Threads.@spawn sleep(10)
timer = Timer(2)
@wait_while !istaskdone(task) && isopen(timer)
istaskdone(task) == false
```
