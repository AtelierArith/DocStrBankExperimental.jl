```
request!(s, r, quantity, request)
request!(s, q, request)
```

Function used to register request for resource in `SimResource` or object from `SimQueue`.

In `SimResource` requested `quantity` must be provided and `request` accepts only `Scheduler` argument (it must know what it wanted). Returns tuple of:

  * `true` if successfull and `false` when too many requests were made
  * `ResourceRequest` object created

In `SimResource` function `request` must accept one argument `Scheduler`. In `SimQueue` function `request` must accept two arguments `Scheduler` and object.
