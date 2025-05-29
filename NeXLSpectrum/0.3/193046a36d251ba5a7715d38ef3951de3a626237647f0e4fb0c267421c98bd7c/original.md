```
maxpixel(hss::HyperSpectrum, filt=ci->true)
maxpixel(hss::HyperSpectrum, cis::CartesianIndices, filt=ci->true)
maxpixel(hss::HyperSpectrum, mask::BitArray)
minpixel(hss::HyperSpectrum, filt=ci->true)
minpixel(hss::HyperSpectrum, cis::CartesianIndices, filt=ci->true)
minpixel(hss::HyperSpectrum, mask::BitArray)
```

Compute Bright's Max-Pixel derived signal for the entire HyperSpectrum or a rectanglar sub-region.
