```
getNeededPoints(tsg::TasmanianSG)
```

returns the points needed to form the interpolant or the next level of refinement following a set***Refinement() call

output: 2-D array of size dimension X getNumNeeded()     each column  corresponds to one point     if (getNumNeeded() == 0): returns zeros(dimensions, 0)
