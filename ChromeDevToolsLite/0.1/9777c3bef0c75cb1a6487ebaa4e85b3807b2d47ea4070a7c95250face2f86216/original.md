```
wait_for_visible(element::ElementHandle; retry_delay::Real = 0.3,
    timeout::Real = 10, visible::Bool = true)
```

Wait for an element to be visible, unless `visible` is false (="invisible" element). Throws a TimeoutError if the timeout is reached.
