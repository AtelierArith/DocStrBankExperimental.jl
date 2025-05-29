```
readGIRFFile(g::GirfEssential, pathX::String, pathY::String, pathZ::String, varName::String, doFilter::Bool)
```

Function to read GIRF files with specific variable name and return a corresponding GIRFEssential object.

# Arguments

  * `pathX::String` - Full path for GIRF MAT-file on X axis
  * `pathY::String` - Full path for GIRF MAT-file on Y axis
  * `pathZ::String` - Full path for GIRF MAT-file on Z axis
  * `varName::String` - Variable name that needs to be read as GIRF data from the MAT-files.
  * `doFilter::Bool` - Whether we filter the GIRF data using Tukey filter

# Outputs

  * g::GirfEssential - Constructed GirfEssential object with read-in data.
