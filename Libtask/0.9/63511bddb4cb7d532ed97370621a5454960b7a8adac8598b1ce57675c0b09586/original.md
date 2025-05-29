```
consume(t::TapedTask)
```

Run `t` until it makes a call to `produce`. If this is the first time that `t` has been called, it starts execution from the entry point. If `consume` has previously been called on `t`, it will resume from the last `produce` call. If there are no more `produce` calls, `nothing` will be returned.
