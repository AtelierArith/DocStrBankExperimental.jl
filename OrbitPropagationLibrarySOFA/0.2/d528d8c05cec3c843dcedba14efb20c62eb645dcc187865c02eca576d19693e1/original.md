```
JD, MJD = datevec2jdate(dateVec; system::Symbol=:UTC)
```

Convert a date vector into Julian Date and Modified Julian Date.

A date vector is a length 6 vector of floats with [year, month, day, hour, minute, seconds]

The `system` keyword argument defines which time system the date vector is in. This can be selected from :UTC (default), :UT1, :TAI, :TT, and :TDB

The return values are Julian Date returned in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector. This  can be found in `(M)JD.epoch`

Derived from SOFA's `cal2jd` and `dtf2d`
