```
suitability(elm::Element, mats::AbstractSet{<:Material}, det::Detector; maxE=30.0e3)
suitability(elm::Element, det::Detector; maxE=30.0e3, minC=0.1)
```

Tabulates the characteristic X-ray peaks for the `Element` for which there are suitable materials  in `mats` for the specified detector.  The second form uses a default set of Materials in the file NeXLCore "standards.txt".

This function is helpful for determining which `Material`s are suitable to act as  fitting standards for the specified Element.  It shows how NeXLSpectrum will break up the  characteristic peaks associated with `elm` into contiguous regions each of which will be  fit independently. NeXLSpectrum attempts to break each element into as many independent  regions as possible dependent on the resolution of the specified `EDSDetector`.  If there is an interference between one of the other elements in the `Material` and `elm` then this peak will not be suitable as a fitting standard.  However, it can be used as a  similar standard.
