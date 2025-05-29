```
SpectralLibrary(file_name::String,
    class_header_name::String,
    spectral_starting_column::Int64=2,
    truncate_end_columns::Int64=0,
    class_valid_keys=nothing,
    scale_factor=1.0,
    wavelength_regions_ignore=[0, 440, 1310, 1490, 1770, 2050, 2440, 2880])
```

Constructor for the `SpectralLibrary` struct.

# Arguments

  * `file_name::String`: Endmember Library data file name, CSV-like.
  * `class_header_name::String`: Column for class labels in data file.
  * `spectral_starting_column::Int64=2`: Column for start of spectral data
  * `truncate_end_columns::Int64=0`: Number of columns to ignore from end of data.
  * `class_valid_keys=nothing`: List of valid class labels.
  * `scale_factor::Float64=1.0`: Spectral scaling factor.
  * `wavelength_regions_ignore=[0,440,1310,1490,1770,2050,2440,2880]`: List of wavelength

regions to ignore as beginning/end pairs in list.
