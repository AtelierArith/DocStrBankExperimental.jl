```
GAST = gast(JD_UT1)
```

Convert a UT1 Julian Date into the GAST at that epoch.

The input values are Julian Date returned in two pieces, in the usual SOFA manner, which is designed to preserve time resolution. The full Julian Date is available as a single number by adding the two components of the vector.

The Greenwich Apparent Sidereal Time is an angle describing the true rotation  of the Prime Meridian from the vernal equinox. There are several implementations, which can be selected by the `model` input, 1982/1994 (`94`,  default), 2000 (`00`) or 2006(`06`).

Derived from SOFA's `gst94`, `gmst00`, and `gmst06`
