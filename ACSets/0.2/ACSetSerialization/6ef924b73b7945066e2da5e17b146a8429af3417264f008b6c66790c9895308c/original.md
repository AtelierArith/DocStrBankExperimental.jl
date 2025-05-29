Read/deserialize an acset from an external source.

Supported source types include:

  * `AbstractDict`: assumed to be JSON data
  * `XLSX.XLSXFile`: Microsoft Excel file (requires XLSX.jl)

# Arguments

  * `cons`: constructor for acset, e.g., the type of a struct acset
  * `source`: source to read from
