```
linescan(hss::HyperSpectrum{T,2,3}, ci1::CartesianIndex{2}, ci2::CartesianIndex{2}, width::Int=1)
```

Extract pixels from `hss` along the line from `ci1` to `ci2` as a 1D HyperSpectrum.  The `width` argument integrates the linescan along a line perpendicular to the primary axis. Only works on 2D SpectrumImages and for odd values of `width`.   The algorithm does double count the occasional pixel but the length of each perpendicular is maintained at `width`. The `AxisArrays.axes(...)` scaling is maintained so lengths on the linescan can be compared to lengths on the original map.
