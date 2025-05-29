```
dat = dat_datevec(dateVec)
```

Return the ΔAT value for the given date vector.

A date vector is a length 6 vector of floats with [year, month, day, hour, minute, seconds]

Requires an update with every new leap second.

Derived from SOFA's `iauDat`
