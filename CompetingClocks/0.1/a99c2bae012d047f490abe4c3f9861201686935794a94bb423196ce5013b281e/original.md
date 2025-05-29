```
FirstToFire{KeyType,TimeType}()
```

This sampler is often the fastest for non-exponential distributions. When a clock is first enabled, this sampler asks the clock when it would fire and saves that time in a sorted heap of future times. Then it works through the heap, one by one. When a clock is disabled, its future firing time is removed from the list. There is no memory of previous firing times.
