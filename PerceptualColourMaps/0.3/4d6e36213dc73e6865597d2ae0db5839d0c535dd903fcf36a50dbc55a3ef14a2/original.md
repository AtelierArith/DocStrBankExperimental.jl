Simple 1D linear interpolation of an array of data

```
 Usage:  yi = interp1(x, y, xi)

Arguments:  x - Array of coordinates at which y is defined.
            y - Array of values at coordinates x.
           xi - Coordinate locations at which you wish to interpolate y values.

Returns:   yi - Values linearly interpolated from y at xi.

```

Interpolates y, defined at values x, at locations xi and returns the corresponding values as yi

x is assumed increasing but not necessarily equi-spaced. xi values do not need to be sorted.

If any xi are outside the range of x then the corresponding value of yi is set to the appropriate end value of y.
