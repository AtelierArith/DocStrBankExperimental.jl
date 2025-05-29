```
LinearInterpolation(u, t; extrapolate = false, safetycopy = true)
```

It is the method of interpolating between the data points using a linear polynomial. For any point, two data points one each side are chosen and connected with a line. Extrapolation extends the last linear polynomial on each side.

## Arguments

  * `u`: data points.
  * `t`: time points.

## Keyword Arguments

  * `extrapolate`: boolean value to allow extrapolation. Defaults to `false`.
  * `safetycopy`: boolean value to make a copy of `u` and `t`. Defaults to `true`.
