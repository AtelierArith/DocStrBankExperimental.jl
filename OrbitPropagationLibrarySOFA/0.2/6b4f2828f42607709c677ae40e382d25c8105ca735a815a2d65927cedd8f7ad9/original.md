```
rotmatrix = mod2j200076_matrix(JD)
```

Find the MOD to J2000 rotation matrix for a given TT Julian Date using the IAU-76 model.

The input values are Julian Date is given in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

Used to transform a MOD vector into J2000 as `r_J2000 = rotMatrix * r_MOD`

Derived from SOFA's `pmat76` and Vallado's description of the IAU-76 reduction.
