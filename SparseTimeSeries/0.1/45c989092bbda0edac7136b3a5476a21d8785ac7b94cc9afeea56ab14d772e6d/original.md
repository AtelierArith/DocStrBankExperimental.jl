```
align(ys::EventSeries{T}...)
```

Returns a tuple of EventSeries containing subsets of the corresponding series input, such that the time domain of each output series corresponds to the largest common time domain of the input series. See `select`.
