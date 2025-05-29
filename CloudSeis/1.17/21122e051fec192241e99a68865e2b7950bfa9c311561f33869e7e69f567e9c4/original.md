```
foldmap(io; all=false, nasync=2048, showprogress=false)
```

Return the foldmap for either the currently cached extent (if `all=false`) or the entire dataset if `all=true`.  If `all=true`, then the operation is performed using an asynchronous map over the extents.  The number of asynchronous tasks in this map is controled by `nasync`.  Use `showprogress=true` to display a progress bar while loading the foldmap.
