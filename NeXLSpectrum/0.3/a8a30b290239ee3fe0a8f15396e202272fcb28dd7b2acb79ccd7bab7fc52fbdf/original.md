```
roiimage(hss::HyperSpectrum, chs::AbstractUnitRange{<:Integer})
```

Create a count map from the specified contiguous range of channels. (Accounts for differences in :LiveTime between pixels.)
