```
xyz(jd[, equinox]) -> x, y, z, v_x, v_y, v_z
```

### Purpose

Calculate geocentric $x$, $y$, and $z$ and velocity coordinates of the Sun.

### Explanation

Calculates geocentric $x$, $y$, and $z$ vectors and velocity coordinates ($dx$, $dy$ and $dz$) of the Sun.  (The positive $x$ axis is directed towards the equinox, the $y$-axis, towards the point on the equator at right ascension 6h, and the $z$ axis toward the north pole of the equator).  Typical position accuracy is $<10^{-4}$ AU (15000 km).

### Arguments

  * `jd`: number of Reduced Julian Days for the wanted date.  It can be either a scalar or a vector.
  * `equinox` (optional numeric argument): equinox of output. Default is 1950.

You can use `juldate` to get the number of Reduced Julian Days for the selected dates.

### Output

The 6-tuple $(x, y, z, v_x, v_y, v_z)$, where

  * $x, y, z$: scalars or vectors giving heliocentric rectangular coordinates (in AU) for each date supplied.  Note that $\sqrt{x^2 + y^2 + z^2}$ gives the Earth-Sun distance for the given date.
  * $v_x, v_y, v_z$: velocity vectors corresponding to $x, y$, and $z$.

### Example

What were the rectangular coordinates and velocities of the Sun on 1999-01-22T00:00:00 (= JD 2451200.5) in J2000 coords?  Note: Astronomical Almanac (AA) is in TDT, so add 64 seconds to UT to convert.

```jldoctest
julia> using AstroLib, Dates

julia> jd = juldate(DateTime(1999, 1, 22))
51200.5

julia> xyz(jd + 64/86400, 2000)
(0.514568709240398, -0.7696326261820209, -0.33376880143023935, 0.014947267514079971, 0.008314838205477328, 0.003606857607575486)
```

Compare to Astronomical Almanac (1999 page C20)

```plain
            x  (AU)        y  (AU)     z (AU)
xyz:      0.51456871   -0.76963263  -0.33376880
AA:       0.51453130   -0.7697110   -0.3337152
abs(err): 0.00003739    0.00007839   0.00005360
abs(err)
    (km):   5609          11759         8040
```

NOTE: Velocities in AA are for Earth/Moon barycenter       (a very minor offset) see AA 1999 page E3

```plain
           x vel (AU/day) y vel (AU/day)   z vel (AU/day)
xyz:      -0.014947268   -0.0083148382    -0.0036068576
AA:       -0.01494574    -0.00831185      -0.00360365
abs(err):  0.000001583    0.0000029886     0.0000032076
abs(err)
 (km/sec): 0.00265        0.00519          0.00557
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
