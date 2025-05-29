```
setdata!(buf::FastReadBuffer, data::AbstractVector{UInt8))
```

Copy the data in `data` to the internal data buffer in `buf` and reset the position to the beginning.
