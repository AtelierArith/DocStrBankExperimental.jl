```
asphericType(surf::AsphericSurface)
```

Query the polynomial type of `asp.  Returns CONIC, ODD, EVEN, or ODDEVEN. CONIC corresponds to no aspheric terms, ODD  means it only has odd aspheric terms, EVEN means only even aspheric terms and ODDEVEN means both even and odd terms. 

This function is to enable proper interpretation of `surf.aspherics` by any optimization routines that directly query the aspheric coefficients.
