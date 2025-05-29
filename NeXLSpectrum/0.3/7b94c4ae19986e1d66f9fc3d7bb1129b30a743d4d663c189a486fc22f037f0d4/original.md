```
roiimages(hss::HyperSpectrum, achs::AbstractVector{<:AbstractUnitRange{<:Integer}})
```

Create an array of Gray images representing the intensity in each range of channels in in `achs`.  They are normalized such the the most intense pixel in any of them defines white. (Accounts for differences in :LiveTime between pixels.)
