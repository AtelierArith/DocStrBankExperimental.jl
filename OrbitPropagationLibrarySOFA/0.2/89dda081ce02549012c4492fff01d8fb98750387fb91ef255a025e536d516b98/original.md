```
rotMatrix = tod2mod76_matrix(JD)
```

Find the TOD to MOD rotation matrix for a given TT Julian Date using the IAU-76 model.

The input values are Julian Date is given in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

Used to transform a TOD vector into MOD as `r_MOD = rotMatrix * r_TOD`

Derived from SOFA's `nutm80` and Vallado's description of the IAU-76 reduction.
