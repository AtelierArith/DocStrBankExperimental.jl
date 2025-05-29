```
WCSGrid(img::AstroImageMat, ax=(1,2), coords=(first(axes(img,ax[1])),first(axes(img,ax[2]))))
```

Given an AstroImageMat, return information necessary to plot WCS gridlines in physical coordinates against the image's pixel coordinates. This function has to work on both plotted axes at once to handle rotation and general curvature of the WCS grid projected on the image coordinates.
