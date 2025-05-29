```
asin!(rop, op, rnd)
```

Set `rop` to the arc-sine of `op`, rounded in the direction `rnd`. Note that since `asin(1)` (resp. `asin(-1)`) returns the floating-point number closest to π/2 (resp -π/2) according to the given rounding mode, this number might not be in the output range `-π/2≤rop<π/2` of the arc-sine function; still, the result lies in the image of the output range by the rounding function.
