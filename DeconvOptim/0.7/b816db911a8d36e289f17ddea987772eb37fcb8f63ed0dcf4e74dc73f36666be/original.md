```
get_indices_around_center(i_in, i_out)
```

A function which provides two output indices `i1` and `i2` where `i2 - i1 = i_out` The indices are chosen in a way that the set `i1:i2` cuts the interval `1:i_in` in a way that the center frequency stays at the center position. Works for both odd and even indices
