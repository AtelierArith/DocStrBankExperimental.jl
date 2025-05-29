```
qmps = MPS(Qlabels[,oc=1,type=Float64])
```

Creates a quantum number MPS `qmps` with quantum numbers assigned from an array of an array of `qnum` (non-uniform and can be shorter than `Ns`, which will cause the program to repeat a shorter number) `Qlabels` with orthogonality center `oc` and data type `type`; `Ns` is the number of sites in the system
