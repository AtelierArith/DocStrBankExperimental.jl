```
@throttle
```

Throttle a `for` loop or `while` loop by calling `sleep` at the beginning of each loop iteration (if necessary), so that a designated variable increases at a rate of at most `max_rate` (compared to wall time).

The first argument that `@throttle` takes is the variable to be rate-limited. This variable must be in scope inside the loop body. The second argument is a for loop or while loop. Optionally, the following keyword arguments may be passed in after the loop argument:

  * `max_rate`: specifies the maximum rate at which the designated variable should

increase. Defaults to `1.`.

  * `min_sleep_time`: specifies the minimum time to sleep (in seconds). Defaults to

`0.01`, and must be at least 0.001 (due to the accuracy of the `sleep` function).

# Examples

```julia
x = 0
@throttle t for t = 1 : 0.01 : 2
    x += 1
end max_rate = 2.
```

will finish in approximately 0.5 seconds.

```julia
x = 0.
@throttle x for i = 0 : 10
    x += 0.1
end
```

will use the default `max_rate` value of `1.` and thus finish in approximately 1 second.

```julia
i = 0
@throttle i while i <= 10
    println(i)
    i += 1
end min_sleep_time=1.5 max_rate=1
```

will print the numbers from 0 to 10 at an average rate of one per second, while never sleeping for less than 1.5 second.
