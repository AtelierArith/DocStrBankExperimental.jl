Wraps a function, causing it to trigger every `n` CFR iterations

```
test_cb = Throttle(() -> println("test"), 100)
```

Above example will print `"test"` every 100 CFR iterations
