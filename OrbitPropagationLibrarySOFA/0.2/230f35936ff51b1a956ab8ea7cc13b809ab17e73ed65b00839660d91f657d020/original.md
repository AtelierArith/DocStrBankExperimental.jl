```
rotMatrix = itrf2pef76_matrix(JD)
```

Find the ITRF to PEF rotation matrix for a given UTC Julian Date using the  IAU-76 model.

The input values are Julian Date is given in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

Used to transform an ITRF vector into PEF as `r_PEF = rotMatrix * r_ITRF`

Derived from Vallado's description of the IAU-76 reduction.
