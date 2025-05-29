```
colorize(hss::HyperSpectrum, cxrs::AbstractVector{CharXRay}, normalize=:All)
```

Create RGB colorized images from up to three `CharXRay` which define channels over which the count signal is integrated. `normalize=:All` puts the intensities on a common scale using the `roiimages(...)` method.  Otherwise each image is scaled independently based on the brightest pixel.
