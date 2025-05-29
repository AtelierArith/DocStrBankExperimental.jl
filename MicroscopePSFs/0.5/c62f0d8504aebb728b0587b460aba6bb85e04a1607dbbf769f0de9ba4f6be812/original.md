```
GaussianPSF(psf::AiryPSF)
```

Convert an AiryPSF to an approximate GaussianPSF by matching the FWHM.

Uses the relationship that σ ≈ 0.22 * λ/NA
