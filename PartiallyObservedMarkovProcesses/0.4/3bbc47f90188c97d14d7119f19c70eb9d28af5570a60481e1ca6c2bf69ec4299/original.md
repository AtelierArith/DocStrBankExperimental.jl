```
rprocess(object; x0, t0 = timezero(object), times=times(object), params = coef(object))
```

`rprocess` is the workhorse for the simulator of the process

If there is no user-supplied *rprocess* component, the dynamics are trivial.
