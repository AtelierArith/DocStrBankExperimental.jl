```
roiimages(hss::HyperSpectrum, cxrs::AbstractVector{CharXRay})
```

Create an array of Gray images representing the intensity in each of the CharXRay lines in `cxrs`.  They are normalized such the the most intense pixel in any of them defines white. By default, integrates for one FWHM at `cxr`.  If hss[:Detector] is an `EDSDetector`, the FWHM  is taken from it.   Otherwise, a FWHM of 130 eV at Mn Kα is assumed.
