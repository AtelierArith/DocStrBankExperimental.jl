```
pxtype(ctx::Context)
```

Return the type of the data in the TIFF file.

# Examples

```jldoctest
ScanImageTiffReader.open(mytif) do io
    pxtype(io)
end
# output
Int16
```
