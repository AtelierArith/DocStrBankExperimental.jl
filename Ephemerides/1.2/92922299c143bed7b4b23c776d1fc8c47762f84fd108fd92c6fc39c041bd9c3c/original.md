```
ephem_timescale_id(eph::EphemerisProvider)
```

Retrieve a timescale ID associated with the ephemeris handler `eph`.  It returns 1 for Barycentric Dynamical Time (TDB) and 2 for Barycentric Coordinate Time (TCB).

!!! warning
    Ephemeris providers with mixed timescales are not supported. An error is thrown if in  the ephemeris handler some segments are defined in TDB and some other segments in TCB.

