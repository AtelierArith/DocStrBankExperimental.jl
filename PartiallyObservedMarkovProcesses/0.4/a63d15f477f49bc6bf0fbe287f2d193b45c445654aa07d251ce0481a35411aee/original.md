```
pfilter(object; Np = 1, params, rinit, rprocess, logmeasure, args...)
```

`pfilter` runs a basic particle filter. At least the `rinit`, `rprocess`, and `logdmeasure` basic components are needed. `args...` can be used to modify or unset additional fields.
