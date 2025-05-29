```
b0map()
```

This version expects masked column-like inputs. For expert use only.

# In

  * `finit (np)` initial estimate in Hz (`np` is # of pixels in mask)
  * `zdata (np, ne)` `ne` sets of coil-combined measurements
  * `sos (np)` sum-of-squares of coil maps
  * `echotime (ne)` vector of `ne` echo time offsets
  * `mask (N)` logical reconstruction mask
