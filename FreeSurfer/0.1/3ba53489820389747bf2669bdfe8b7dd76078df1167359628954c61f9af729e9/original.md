```
mri_write(mri::MRI, outfile::String, datatype::DataType=Float32)
```

Write an MRI volume to disk. Return true is an error occurred (i.e., the number of bytes written were not as expected based on the size of the volume).

# Arguments

  * `mri::MRI`: A structure like that returned by `mri_read()`. The geometry (i.e., direction cosines, voxel resolution, and P0) are all recomputed from mri.vox2ras0. So, if a method has changed one of the other fields, e.g., mri.x_r, this change will not be reflected in the output volume.
  * `outfile::String`: Path to the output file, which can be:

    1. An MGH file, e.g., f.mgh or f.mgz (uncompressed or compressed)
    2. A NIfTI file, e.g., f.nii or f.nii.gz (uncompressed or compressed).
  * `datatype::DataType=Float32`: Only applies to NIfTI and can be UInt8, Int16, Int32, Float32, Float64, Int8, UInt16, UInt32.
