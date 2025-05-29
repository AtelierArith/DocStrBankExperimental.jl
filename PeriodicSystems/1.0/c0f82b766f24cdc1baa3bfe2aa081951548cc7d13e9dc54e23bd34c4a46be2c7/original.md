```
psteval(psys,tval) -> sys::DescriptorStateSpace
```

Compute for the periodic system `psys = (A(t),B(t),C(t),D(t))` and a time value `tval`,  the LTI system `sys = (A(tval),B(tval),C(tval),D(tval))`. If `A(tval)` is not square, then  `A(tval)` is padded with zeros to form a square matrix and appropriate numbers of zero rows and zero columns are added to  `B(tval)` and `C(tval)`, respectively. 
