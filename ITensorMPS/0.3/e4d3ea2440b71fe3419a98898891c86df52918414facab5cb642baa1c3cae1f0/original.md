```
product(P::ProjMPO,v::ITensor)::ITensor

(P::ProjMPO)(v::ITensor)
```

Efficiently multiply the ProjMPO `P` by an ITensor `v` in the sense that the ProjMPO is a generalized square matrix or linear operator and `v` is a generalized vector in the space where it acts. The returned ITensor will have the same indices as `v`. The operator overload `P(v)` is shorthand for `product(P,v)`.
