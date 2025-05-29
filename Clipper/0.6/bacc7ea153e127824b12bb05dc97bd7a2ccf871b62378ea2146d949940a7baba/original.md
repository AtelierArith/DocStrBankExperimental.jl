```
IntPoint(x, y)
```

Create an IntPoint from integer values.

```
IntPoint(x, y, magnitude, precision)
```

Create an IntPoint from floating point values with the given number of digits of precision. magnitude = number of digits above zero (90 => 2, 9 => 1, 0.9 => 0, 0.09 => -1) sigdigits = number of digits to preserve (94.3856 with 4 => 94.39)

```julia
a = IntPoint(5.483, 55.8739, 2, 4) # [548, 5587]
b,c = tofloat(a, 2, 4)             # 5.48, 55.87
```
