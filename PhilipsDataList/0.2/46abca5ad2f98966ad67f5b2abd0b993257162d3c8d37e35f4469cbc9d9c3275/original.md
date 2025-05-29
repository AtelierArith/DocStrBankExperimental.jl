```
data_list_to_kspace(path_to_data_or_list; drop_dims=true,
remove_readout_oversampling=false, offset_array=false)
```

Read in the .{data/list} files and store the measured "STD" samples in a k-space.

This is the main entry point for converting Philips .data/.list files to a k-space array. It handles reading, parsing, and assembling the data, and provides options for dimension handling and oversampling removal.

## Warning

This function should only be used on data from Cartesian acquisitions. I don't know what exactly happens for non-Cartesian data.

## Note

  * It is assumed that each readout has the same number of samples.
  * The .data and .list file should have the same name (except for the extension). The `path` is not required to have an extension since this function will append .data and .list to the path to read the respective files.
  * The k-space has named dimensions (it is a `NamedDimsArray`) which allows, for example, to

retrieve all samples from a channel with index `i` by indexing with `kspace[chan=i]`.

  * The ordering of the dimensions is the same as in the `DIMENSIONS_STD` constant. However, if `drop_dims=true`, dimensions of size 1 are dropped.
  * If `offsetarray` is `true`, the k-space is stored as an OffsetArray s.t. we can use the ranges contained in the list file as indices. For example, `kspace[kx=0, ky=0, kz=0, ...]` will give the k-space value(s) at the center of k-space.
  * If `remove_readout_oversampling` is `true`, the readout oversampling is removed by cropping the k-space and applying an ifft along the readout direction.
