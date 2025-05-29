```
sysi = innovation_form(sys, R1, R2[, R12])
sysi = innovation_form(sys; sysw=I, syse=I, R1=I, R2=I)
```

Takes a system

```
x' = Ax + Bu + w ~ R1
y  = Cx + Du + e ~ R2
```

and returns the system

```
x' = Ax + Kv
y  = Cx + v
```

where `v` is the innovation sequence.

If `sysw` (`syse`) is given, the covariance resulting in filtering noise with `R1` (`R2`) through `sysw` (`syse`) is used as covariance.

See Stochastic Control, Chapter 4, Åström
