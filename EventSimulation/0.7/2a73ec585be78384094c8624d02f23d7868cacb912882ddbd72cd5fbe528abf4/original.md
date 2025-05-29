```
provide!(s, r, quantity)
provide!(s, q, object)
```

Allows to fill `SimResource` with `quantity` or `SimQueue` with `object`.

In `SimResource` changes the balance of `r.quantity`. Given quantity may be any number, but the balance of `SimResource` will be changed only in `lo`-`hi` range. Returns the actual change in `SimResource` balance.

In `SimQueue` adds `object` to `q.queue`. Returns `true` on success and `false` if there were too many objects in queue already.
