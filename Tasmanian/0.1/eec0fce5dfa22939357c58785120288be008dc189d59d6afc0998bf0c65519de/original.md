```
getLoadedPoints(tsg::TasmanianSG)
```

returns the points loaded in the existing interpolant

output: matrix of size getNumDimensions() X getNumNeeded()     each column  corresponds to one point     if getNumLoaded() == 0, returns zeros(2)
