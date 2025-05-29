```
length(ctx::Context)
```

Return the number of planes in the image stack.

# Examples

```jldoctest
ScanImageTiffReader.open(mytif) do io
    length(io)
end
# output
10
```
