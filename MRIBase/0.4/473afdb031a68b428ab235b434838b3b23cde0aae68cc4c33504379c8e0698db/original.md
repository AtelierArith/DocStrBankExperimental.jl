```
AcquistionData(kdata::Array{T,6})
```

Returns an AcquisitionData struct created from a zero-filled kspace with 6 dimensions :     [x,y,z,channels,echoes,repetitions]

Different undersampling patterns can be handled **only** along the echo dimension.

This methods assumes the data to correspond to a single volume encoded with a 3d Cartesian sequence.
