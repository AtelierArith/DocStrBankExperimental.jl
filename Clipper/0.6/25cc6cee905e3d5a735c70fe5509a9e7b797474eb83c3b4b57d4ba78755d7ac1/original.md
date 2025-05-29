```
tofloat(intpoint, magnitude, precision)
```

Restore an IntPoint to floating point values using the specified magnitude and precision. magnitude = number of digits to be above zero (90 => 2, 9 => 1, 0.9 => 0, 0.09 => -1) sigdigits = number of digits that were preserved (94.3856 with 4 => 94.39)
