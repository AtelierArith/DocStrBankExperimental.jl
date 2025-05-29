```
dose(hss::HyperSpectrum) # Average dose per pixel
dose(hss::HyperSpectrum, idx...) # Dose for the `idx` pixel
```

Returns the product of the probe current and the live-time on a per pixel basis.
