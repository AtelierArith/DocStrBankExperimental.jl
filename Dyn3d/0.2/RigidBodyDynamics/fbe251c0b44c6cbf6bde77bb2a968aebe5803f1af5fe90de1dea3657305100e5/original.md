```
HERKFuncG(bs, sys)
```

HERKFuncG constructs the input function G for HERK method. It returns the motion constraint matrix acting on all body's velocity. These constraints arise from body velocity relation in each body's local body coord, for example if body 2 and 3 are connected then:    v(3) = vJ(3) + X2*to*3*v(2)
