```
addtraces!(p::Plot, i::Int, traces::AbstractTrace...)
```

Add trace(s) at a specified location in the Plot's array of data.

The new traces will start at index `p.data[i]`
