```
count_down(latch::CountDownLatch)
```

Counts down the `latch` once. This may cause the count to become negative. Any tasks that were blocked in `await` will be woken if the count becomes `<= 0`.
