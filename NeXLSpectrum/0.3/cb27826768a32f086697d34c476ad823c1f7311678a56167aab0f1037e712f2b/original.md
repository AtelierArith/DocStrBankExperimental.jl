```
indexofmaxpixel(hss::HyperSpectrum, ch::Int) # at channel `ch`
indexofmaxpixel(hss::HyperSpectrum) # all channels
indexofmaxpixel(hss::HyperSpectrum, ch::Int, cis::CartesianIndices)
indexofmaxpixel(hss::HyperSpectrum, cis::CartesianIndices)
```

Find the indices producing the maximum value in data[ch] or data[:] within 'cis' or full spatial dimensions.
