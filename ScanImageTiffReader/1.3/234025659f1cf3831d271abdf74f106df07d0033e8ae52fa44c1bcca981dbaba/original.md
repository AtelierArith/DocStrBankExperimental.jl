```
metadata(ctx::Context)
```

Read the ScanImage metadata section from the file.

This data section is not part of the Tiff specification, so common Tiff readers will not be able to access this data.

In ScanImage 2016 and later, this is a JSON string.  For previous versions of ScanImage, this is a bytestring that must be deserialized in MATLAB.

# Examples

```jldoctest
ScanImageTiffReader.open(mytif) do io
    JSON.parse(metadata(io))
end
# output
Dict{String,Any} with 2 entries:
  "SI"        => Dict{String,Any}("hConfigurationSaver"=>Dict{String,Any}("usrF…
  "RoiGroups" => Dict{String,Any}("photostimRoiGroups"=>nothing,"imagingRoiGrou…
```
