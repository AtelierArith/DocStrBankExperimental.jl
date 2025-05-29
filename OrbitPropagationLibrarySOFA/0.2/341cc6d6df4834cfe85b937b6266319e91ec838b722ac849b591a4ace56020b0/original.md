```
rotMatrix = pef2tod76_matrix(JD)
```

Find the PEF to TOD rotation matrix for a given UT1 Julian Date using the IAU-76 model.

The input values are Julian Date is given in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

Used to transform a PEF vector into TOD as `r_TOD = rotMatrix * r_PEF`

Derived from Vallado's description of the IAU-76 reduction.
