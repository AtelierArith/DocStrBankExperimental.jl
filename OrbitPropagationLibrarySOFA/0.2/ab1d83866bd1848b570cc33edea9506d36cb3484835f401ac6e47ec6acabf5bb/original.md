```
r_MOD = j20002mod76(r_j2000, JD)
```

Transform a J2000 vector into MOD at the given TT Julian Date using the IAU-76  model.

The state vector must be of length 3.

The input Julian Date is given in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

Derived from SOFA's `pmat76` and Vallado's description of the IAU-76 reduction.
