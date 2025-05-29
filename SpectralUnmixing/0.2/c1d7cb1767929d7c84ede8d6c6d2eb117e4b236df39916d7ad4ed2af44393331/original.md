```
read_envi_wavelengths(filename::String, nm::Bool=true)
```

Read wavelength data from an ENVI header file with option to convert from microns to nanometers.

  * If no wavelengths are found, returns `nothing`.

# Notes

  * The function constructs the expected header filename by replacing the extension of the

given filename with `.hdr`.

  * This function logs an error if no wavelength data is found in the header file.
