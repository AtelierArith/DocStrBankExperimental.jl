```
GMST = gmst(JD_UT1)
```

Convert a UT1 Julian Date into the GMST at that epoch.

The input values are Julian Date returned in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

The Greenwich Mean Sidereal Time is an angle describing the mean rotation of the Prime Meridian from the vernal equinox. There are several implementations, which can be selected by the `model` input, 1982 (`82`, default), 2000 (`00`) or 2006(`06`).

Derived from SOFA's `gmst82`, `gmst00`, and `gmst06`
