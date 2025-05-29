```
xc, yc, R, err = circfit(x,y; taubin=false)
```

Fits a circle in the x,y plane.

From FEX contribution https://www.mathworks.com/matlabcentral/fileexchange/5557-circle-fit

### Arguments

  * `xy`: a Mx2 matrix or GMTdataset with x,y coordinates of n points
  * `x,y`: Alternatively, pass two vectors where each (x(i),y(i)) is a given point

### Options

  * `taubin`: If $true$, use the Taubin algorithm instead. https://people.cas.uab.edu/~mosya/cl/TaubinSVD.m recomends this as best alghoritm. ~2x slower than the default method.

### Returns

  * `xc`, `yc`, `R`, `err`; The center, radius and the error of the fit
