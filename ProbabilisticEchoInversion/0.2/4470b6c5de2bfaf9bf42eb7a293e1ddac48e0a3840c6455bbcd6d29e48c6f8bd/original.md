```
iterspectra(echogram[, freqdim])
```

Given an mulifrequency or broadband echogram in the form of a `DimArray`, with the acoustic frequencies in one dimension (by default named `:F`), iterate over each spectrum. The iterator yields `NamedTuples` with three fields: 

  * `coords`: Coordinates of the spectrum on the non-`:F` dimensions of the Array   (i.e. its location space/time)
  * `freqs`: Array of acoustic frequencies
  * `backscatter`: Array of backscatter values
