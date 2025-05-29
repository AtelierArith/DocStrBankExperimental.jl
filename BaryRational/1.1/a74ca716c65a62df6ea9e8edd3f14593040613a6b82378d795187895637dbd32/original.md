```
floater_weights(x, d=0)
```

Calculate the Floater-Hormann weights for grid x and mixing degree d.  For many applications d = 3 or 4 works well.

```
if we had a regular grid the values would be...
x: points at which we have function values
d: mixing degree        weights
d = 0                 1,1,...,1,1  
d = 1               1,2,2,...,2,2,1
d = 2             1,3,4,4,...,4,4,3,1
d = 3           1,4,7,8,8,...,8,8,7,4,1
d = 4     1,5,11,15,16,16,...,16,16,15,11,5,1
```

But note, if you do have a regularly spaced grid, it is much better to call the floater_weights(n, order)
