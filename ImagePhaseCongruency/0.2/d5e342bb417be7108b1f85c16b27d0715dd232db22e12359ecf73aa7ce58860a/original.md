Generate geometric series.

Useful for generating geometrically scaled wavelengths for specifying filter banks.

```
Usage 1: s = geoseries(s1, mult, n)

Arguments:      s1 - The starting value in the series.
              mult - The scaling factor between succesive values.
                 n - The desired number of elements in the series.

Usage 2: s = geoseries((s1, sn), n)

Arguments: (s1, sn) - Tuple specifying the 1st and last values
                      in the the series.
                  n - The desired number of elements in the series.
```

Example:

```
      s = geoseries(0.5, 2, 4)
      s =  [0.5000,    1.0000,    2.0000,    4.0000]
```

Alternatively obtain the same series using

```
           s = geoseries((0.5, 4), 4)
```
