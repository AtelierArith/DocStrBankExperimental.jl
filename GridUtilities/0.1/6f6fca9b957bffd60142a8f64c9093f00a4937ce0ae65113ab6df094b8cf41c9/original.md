```
History(datatype,[;htype::HistoryType = RegularHistory])
```

Create an empty history data vector with entries of type `datatype`. Alternatively, one can pass an example instance of the type of entry. An optional argument `htype` specifies the type of history vector. By default, this is `RegularHistory`, but can be alternatively set to `PeriodicHistory`. In the latter case, if the history vector has length `n`, then it will be assumed that the `n+1` entry is identical to the `1` entry.

It is important to note that, in order to use the routines for `History` types, then the element type `datatype` must be outfitted with basic operations: `+`, `-`, scalar multiplication, and `fill!`.

Another constructor is `History(h::History)`, which creates an empty instance of a history of the same type as `h`.
