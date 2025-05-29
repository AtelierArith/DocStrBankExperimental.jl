Abstract type for geodetic datums

A datum is a set of reference objects and assigned coordinates, relative to which other objects may be positioned.  We model these in code with subtypes of `Datum`.  Each geodetic datum has an associated ellipsoid model of the Earth which is required when transforming between coordinate systems.  The ellipsoid can be accessed with the `ellipsoid()` function.
