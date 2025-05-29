```
interrupt!(s, a)
```

First occurrence of `Action` `a` is replaced by no-op in event queue. This way there is no need to fix heap in this operation and it is fast. Returns `true` if `a` was found in queue and `false` otherwise.
