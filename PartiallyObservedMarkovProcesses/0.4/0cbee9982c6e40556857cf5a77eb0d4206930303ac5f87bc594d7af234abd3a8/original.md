```
logdmeasure!(object, ell; times=times(object), y=obs(object), x=states(object), params=coef(object))
```

`logdmeasure!` is the in-place version of the `logdmeasure` workhorse.
