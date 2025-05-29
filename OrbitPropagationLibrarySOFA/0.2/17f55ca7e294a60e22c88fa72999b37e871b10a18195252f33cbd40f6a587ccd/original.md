```
r_TOD = pef2tod76(r_pef, JD)
```

Transform a PEF vector into TOD at the given UT1 Julian Date using the IAU-76  model.

The state vector must be of length 3.

The input Julian Date is given in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

Derived from Vallado's description of the IAU-76 reduction.
