```
acos!(rop, op, rnd)
```

Set `rop` to the arc-cosine of `op`, rounded in the direction `rnd`. Note that since `acos(-1)` returns the floating-point number closest to π according to the given rounding mode, this number might not be in the output range `0≤rop<π` of the arc-cosine function; still, the result lies in the image of the output range by the rounding function.
