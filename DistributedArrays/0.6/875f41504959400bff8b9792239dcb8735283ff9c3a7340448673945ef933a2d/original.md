```
localpart(d::DArray)
```

Get the local piece of a distributed array. Returns an empty array if no local part exists on the calling process.

d[:L], d[:l], d[:LP], d[:lp] are an alternative means to get localparts. This syntaxt can also be used for assignment. For example, `d[:L]=v` will assign `v` to the localpart of `d`.
