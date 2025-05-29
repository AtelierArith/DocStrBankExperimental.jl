```
convertUndersampledData(acqData::AcquisitionData)
```

converts undersampled AcquisitionData, where only profiles contained in acqData.subsampleIndices are sampled, into a format where trajectories only contain the sampled profiles.
