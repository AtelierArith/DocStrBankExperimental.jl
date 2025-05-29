```
sysi = innovation_form(sys, K)
```

Takes a system

```
x' = Ax + Bu + Kv
y  = Cx + Du + v
```

and returns the system

```
x' = Ax + Kv
y  = Cx + v
```

where `v` is the innovation sequence.

See Stochastic Control, Chapter 4, Åström
