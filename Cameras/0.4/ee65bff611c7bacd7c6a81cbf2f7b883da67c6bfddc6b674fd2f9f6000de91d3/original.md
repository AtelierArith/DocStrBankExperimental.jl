```
take!(camera::Camera)
```

Take an image, i.e. an [`AbstractAcquiredImage`](@ref). Blocks until an image is available.

Throws [`InvalidStateException`](@ref) if/when camera is stopped.
