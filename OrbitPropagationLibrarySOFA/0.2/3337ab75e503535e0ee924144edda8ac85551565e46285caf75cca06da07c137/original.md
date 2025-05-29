```
r_PEF = pef2itrf76(r_ITRF, JD)
```

Transform a PEF vector into ITRF at the given UTC Julian Date using the IAU-76  model.

The state vector must be of length 3.

The input Julian Date is given in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

Derived from Vallado's description of the IAU-76 reduction.
