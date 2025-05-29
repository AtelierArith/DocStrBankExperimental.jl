```
loadjets(filename; splitby=isspace, constructor=(px,py,pz,E)->LorentzVectorHEP(E,px,py,pz), VT=LorentzVector)
```

Load jets from a file.

# Arguments

  * `filename`: The name of the file to load jets from.
  * `splitby`: The delimiter used to split the data in the file. Default is `isspace`.
  * `constructor`: A function that constructs a `VT` object from the jet data. Default is `(px,py,pz,E)->LorentzVector(E,px,py,pz)`.
  * `VT`: The type of the vector used to store the jet data. Default is `LorentzVector`.

# Returns

  * A vector of `VT` objects representing the loaded jets.
