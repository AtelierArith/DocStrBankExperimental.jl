```
TIFFDataset(fnames::AbstractVector{<:AbstractString};
            aggdim=name, isnewdim=false)
```

Concatenate TIFF files `fnames` along the dimension specified with `aggdim`. The parameter `isnewdim` must be true for new dimensions not initially present in the file. See CommonDataModel.MFDataset for more information of the arguments.
