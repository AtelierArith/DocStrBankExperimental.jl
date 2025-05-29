```
preserve(signal::Signal)
```

prevents `signal` from being garbage collected as long as any of its parents are around. Useful for when you want to do some side effects in a signal. e.g. `preserve(map(println, x))` - this will continue to print updates to x, until x goes out of scope. `foreach` is a shorthand for `map` with `preserve`.
