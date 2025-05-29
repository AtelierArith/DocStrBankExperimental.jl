```
mri_read(infile::String; headeronly::Bool=false, permutedata::Bool=false, reco::Integer=1)
```

Read an image volume from disk and return an `MRI` structure similar to the FreeSurfer MRI struct defined in mri.h.

# Arguments

  * `infile::String`: Path to the input, which can be:

    1. An MGH file, e.g., f.mgh or f.mgz
    2. A NIfTI file, e.g., f.nii or f.nii.gz
    3. A file stem, in which case the format and full file name are determined by finding a file on disk named `infile`.{mgh, mgz, nii, nii.gz}
    4. A Bruker scan directory, which is expected to contain the following files: method, acqp, pdata/1/reco, pdata/1/2dseq

# Optional arguments

  * `headeronly::Bool=false`: If true, the pixel data are not read in.
  * `permutedata::Bool==false`: If true, the first two dimensions of the image volume are permuted in the .vol, .volsize, and .volres fields of the output structure (this is the default behavior of the MATLAB version). The `permutedata` will not affect the vox2ras matrices, which always map indices in the (column, row, slice) convention.
  * `reco::Integer=1`: (Only relevant to reading Bruker scan directories) Number of image reconstruction to load, where 1 denotes the online reconstruction and higher numbers denote any additional offline reconstructions performed after acquisition.

# Output

In the `MRI` structure:

  * Times are in ms and angles are in radians.
  * `vox2ras0`: This field contains the vox2ras matrix that converts 0-based (column, row, slice) voxel indices to (x, y, z) coordinates. This is the also the matrix that mri_write() uses to derive all geometry information (e.g., direction cosines, voxel resolution, P0). Thus if any other geometry fields of the structure are modified, the change will not be reflected in the output volume.
  * `vox2ras1`: This field contains the vox2ras matrix that converts 1-based (column, row, slice) voxel indices to (x, y, z) coordinates.
  * `niftihdr`: If the input file is NIfTI, this field contains a `NIfTIheader` structure.
