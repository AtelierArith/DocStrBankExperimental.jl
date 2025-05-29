```
size(ctx::Context)
```

Return the shape of the data in the TIFF file.

# Examples

```jldoctest
ScanImageTiffReader.open(mytif) do io
    size(io)
end
# output
(512, 512, 10)
```
