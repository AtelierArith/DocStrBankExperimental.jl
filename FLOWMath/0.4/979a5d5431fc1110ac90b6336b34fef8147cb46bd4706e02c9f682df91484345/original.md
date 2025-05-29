```
Akima(xdata, ydata, delta_x=0.0)
```

Creates an akima spline at node points: `xdata`, `ydata`.  This is a 1D spline that avoids overshooting issues common with many other polynomial splines resulting in a more natural curve.  It also only depends on local points (`i-2`...`i+2`) allow for more efficient computation.

`delta_x` is the half width of a smoothing interval used for the absolute value function.  Set `delta_x=0` to recover the original akima spline.  The smoothing is only useful if you want to differentiate xdata and ydata.  In many case the nodal points are fixed so this is not needed.

`eps` is a cutoff used to avoid dividing by zero in the weighting function. Default is `1e-30` but this could be raised to machine precision in some cases to improve derivatives. (E.g., when the denominator in line 105 is very small.)

Returns an akima spline object (Akima struct). This function only performs construction of the spline, not evaluation. This is useful if you want to evaluate the same mesh at multiple different conditions. A convenience method exists below to perform both in one shot.
