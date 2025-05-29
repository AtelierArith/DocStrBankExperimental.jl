```
psys = psappend(psys1, psys2)
```

Append the periodic systems `psys1` and `psys2` by concatenating their input and output vectors.  This corresponds to build `psys` as the block diagonal concatenation of their transfer maps. 
