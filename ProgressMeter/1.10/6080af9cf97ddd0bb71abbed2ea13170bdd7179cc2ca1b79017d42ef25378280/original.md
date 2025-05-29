```
@showprogress [desc="Computing..."] for i = 1:50
    # computation goes here
end

@showprogress [desc="Computing..."] pmap(x->x^2, 1:50)
```

displays progress in performing a computation.  You may optionally supply a custom message to be printed that specifies the computation being performed or other options.

`@showprogress` works for loops, comprehensions, and `map`-like functions. These `map`-like functions rely on `ncalls` being defined and can be checked with `methods(ProgressMeter.ncalls)`. New ones can be added by defining `ProgressMeter.ncalls(::typeof(mapfun), args...) = ...`.

`@showprogress` is thread-safe and will work with `@distributed` loops as well as threaded or distributed functions like `pmap` and `asyncmap`.
