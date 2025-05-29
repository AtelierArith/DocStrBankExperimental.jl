```
sensorsize(model::AbstractCameraModel)
```

Return the size of the camera sensor. By default calling out to columns(model) and rows(model) to build an SVector{2}

`sensorsize(cameramodel::AbstractCameraModel) = SVector{2}(columns(cameramodel), rows(cameramodel))`
