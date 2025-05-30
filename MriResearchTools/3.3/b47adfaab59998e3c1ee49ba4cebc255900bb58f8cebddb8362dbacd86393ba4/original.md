```
robustrescale(array, newmin, newmax; threshold=false, mask=trues(size(array)), datatype=Float64)
```

Rescales the image to the the new range, disregarding outliers. Only values inside `mask` are used for estimating the rescaling option
