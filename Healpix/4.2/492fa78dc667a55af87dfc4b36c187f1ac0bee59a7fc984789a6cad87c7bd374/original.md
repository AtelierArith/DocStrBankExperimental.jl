```
combinemaps{T, O, H}(destmap::HealpixMap{T, O}, desthitmap::HealpixMap{H, O}, othermap::HealpixMap{T, O}, otherhitmap::HealpixMap{H, O})
```

Sum "othermap" to "destmap", assuming that both maps have been produced by binning TODs. The parameters `desthitmap` and `otherhitmap` are the two hit maps. At the end of the call, `destmap` and `desthitmap` are updated.
