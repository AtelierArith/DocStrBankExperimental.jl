```
rampon(x,[len=10ms],[fn=x -> sinpi(0.5x)])
```

Ramp the onset of a signal, smoothly transitioning from 0 to full amplitude over the course of `len` seconds. 

The function determines the shape of the ramp and should be non-decreasing with a range of [0,1] over the domain [0,1]. It should map over the entire range: that is `fn(0) == 0` and `fn(1) == 1`.

Both `len` and `fn` are optional arguments: either one or both can be specified, though `len` must occur before `fn` if present.
