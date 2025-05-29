```
rotMatrix = teme2tod_matrix(JD)
```

Find the TEME to TOD rotation matrix for a given TT Julian Date using the IAU-76 model.

The input values are Julian Date is given in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

Used to transform a TEME vector into TOD as `r_TOD = rotMatrix * r_TEME`

Derived from Vallado's description of the TEME frame. Note that TEME is not  fully defined publicly, and may carry some errors due to the ambiguous nature  of its definition.
