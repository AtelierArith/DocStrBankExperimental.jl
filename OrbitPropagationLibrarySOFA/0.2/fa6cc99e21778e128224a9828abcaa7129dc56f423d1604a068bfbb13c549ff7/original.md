```
DAT = dat(MJD::MJDate)
```

Return the ΔAT value for the given MJD.

The input MJD values are Modified Julian Date returned in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full  Julian Date is available as a single number by adding the two components of the vector. 

Requires an update with every new leap second.

Derived from SOFA's `iauDat`
