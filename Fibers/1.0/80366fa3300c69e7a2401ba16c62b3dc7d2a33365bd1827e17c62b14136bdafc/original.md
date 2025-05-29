```
xfm_apply(xfm::Xform{Tx}, point::Array{Ti})
```

Apply a transform specified in an `Xform` structure to N points specified in a voxel coordinate array of length 3*N, and return the transformed points as a voxel coordinate array of the same shape as the input array
