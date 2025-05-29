```
r_TOD = teme2tod(r_teme, JD)
```

Transform a TEME vector into TOD at the given TT Julian Date using the IAU-76  model.

The state vector must be of length 3.

The input Julian Date is given in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

Derived from Vallado's description of the TEME frame. Note that TEME is not  fully defined publicly, and may carry some errors due to the ambiguous nature  of its definition.
