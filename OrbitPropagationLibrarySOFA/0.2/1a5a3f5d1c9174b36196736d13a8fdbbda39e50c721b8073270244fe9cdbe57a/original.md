```
v_PEF = tod2pef76_vel(v_TOD, r_PEF, JD)
```

Transform a TOD velocity vector into PEF at the given UT1 Julian Date using the  IAU-76 model.

The state vector must be of length 3.

Note that while the velocity vector is given in TOD, the position vector is  given in PEF.

The input Julian Date is given in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

Derived from Vallado's description of the IAU-76 reduction.
