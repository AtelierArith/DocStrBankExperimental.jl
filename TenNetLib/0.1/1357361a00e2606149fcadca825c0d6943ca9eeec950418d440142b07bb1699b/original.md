```
macro threaded_loop(code)
```

Conditional threaded loop by `Threads.@threads`. If `using_threaded_loop()` returns true, performs parallel loop, otherwise performs serial loop.

Note: All other forms of parallelization are switched off inside the loop body, if parallel loop is being executed.

#### Example:

```
@threaded_loop for i = 1 : N
    # Do stuff in parallel
end
```
