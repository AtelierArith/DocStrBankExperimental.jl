```
roiimage(hss::HyperSpectrum, cxr::CharXRay)
```

Create a count map for the specified characteristic X-ray.  By default, integrates for one FWHM at `cxr`.  If hss[:Detector] is an `EDSDetector`, the FWHM is taken from it. Otherwise, a FWHM of 130 eV at Mn Kα is assumed.
