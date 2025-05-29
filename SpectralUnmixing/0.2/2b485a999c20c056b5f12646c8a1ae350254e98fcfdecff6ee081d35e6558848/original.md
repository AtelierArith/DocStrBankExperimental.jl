```
initiate_output_datasets(output_files::Vector{String}, x_len::Int64, y_len::Int64,
                         output_bands::Vector, reference_dataset::ArchGDAL.IDataset)
```

Initialize multiple output raster datasets in ENVI format with specified dimensions and band information using a reference dataset for projection and geotransformation.

# Arguments

  * `output_files::Vector{String}`: File paths of the output datasets. Each entry corresponds

to a separate output raster.

  * `x_len::Int64`: Width of the output datasets.
  * `y_len::Int64`: Height of the output datasets.
  * `output_bands::Vector`: Number of bands for each output dataset. The length of this

vector must match the length of `output_files`.

  * `reference_dataset::ArchGDAL.IDataset`: Reference dataset object from which projection

and geotransformation information will be copied.

# Notes

  * All bands in the output datasets are initialized with the no-data value of `-9999`.
