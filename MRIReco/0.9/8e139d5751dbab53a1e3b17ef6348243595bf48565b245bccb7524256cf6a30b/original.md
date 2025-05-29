```
reconstruction(acqData::AcquisitionData, recoParams::Dict,filename::String; force=false)
```

performs the same image reconstrucion as `reconstruction(acqData::AcquisitionData, recoParams::Dict)` and saves the image in a file with name `filename`. If `force=false`, the reconstructed image is loaded from the the file `filename` if the latter is present.
