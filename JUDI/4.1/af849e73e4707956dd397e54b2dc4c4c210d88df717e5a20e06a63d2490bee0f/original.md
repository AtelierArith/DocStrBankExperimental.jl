```
find_water_bottom(v; eps=1e-4)
```

Fund water bottom based on (x, y) or (x, y, z) input array by finding the first value for each vertical trace that is not close to the top value (first value such that m[x,y,z] > m[x,y,1] for each x, y)
