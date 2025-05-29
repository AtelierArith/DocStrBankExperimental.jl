```
atan2!(rop, y, x, rnd)
```

Set `rop` to the arc-tangent2 of `y` and `x`, rounded in the direction `rnd`: if x > 0, `atan2(y, x) = atan(y/x)`; if x < 0, `atan2(y, x) = sign(y)*(π - atan(|y/x|))`, thus a number from `−π` to `π`. As for `atan`, in case the exact mathematical result is `+π` or `−π`, its rounded result might be outside the function output range.
