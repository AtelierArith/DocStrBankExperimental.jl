```
reconstruction(acqData::AcquisitionData, recoParams::Dict)
```

Performs image reconstruction of an AcquisitionData object. Parameters are specified in a dictionary.

Reconstruction types are specified by the symbol `:reco`. Valid reconstruction names are:

  * :direct - direct Fourier reconstruction
  * :standard           - iterative reconstruction for all contrasts, coils & slices independently
  * :multiEcho          - iterative joint reconstruction of all echo images
  * :multiCoil          - SENSE-type iterative reconstruction
  * :multiCoilMultiEcho - SENSE-type iterative reconstruction of all echo images
