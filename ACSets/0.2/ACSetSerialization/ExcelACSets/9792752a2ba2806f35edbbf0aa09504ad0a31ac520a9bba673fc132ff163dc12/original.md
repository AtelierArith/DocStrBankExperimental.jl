Read acset from an Excel (.xlsx) file.

This is a convenience function that loads the Excel file and then calls [`read_acset`](@ref). To use this function, the package XLSX.jl must be installed and imported.

# Arguments

  * `cons`: constructor for acset, e.g., the acset type for struct acsets
  * `source`: filename or IO stream from which to read Excel file
  * `tables=(;)`: dictionary or named tuple mapping object names in acset schema to Excel table specifications
