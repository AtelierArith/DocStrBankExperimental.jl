```
timedim(img) -> d::Int
```

Return the dimension of the array used for encoding time, or 0 if not using an axis for this purpose.

Note: if you want to recover information about the time axis, it is generally better to use `timeaxis`.
