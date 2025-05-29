```
dmapreduce(dInfo1::Dinfo, dInfo2::Dinfo, map, fold)
```

Variant of `dmapreduce` that works with more `Dinfo`s at once.  The data must be distributed on the same set of workers, in the same order.
