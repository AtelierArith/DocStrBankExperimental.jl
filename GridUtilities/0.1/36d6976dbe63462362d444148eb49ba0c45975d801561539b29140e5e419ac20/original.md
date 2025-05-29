```
store_data!(data,t,S::StorePlan,v)
```

Check whether time `t` is a time for saving for storage as described by plan `S`, and if so, push the variables specified in `v` (a list of pairs) onto the `data` stack. Note that a deepcopy of the values of each variable are stored automatically.
