```
description(ctx::Context, iframe::Int)
```

Return the contents of the image description tag for frame `iframe`.

# Examples

```jldoctest
desc = ScanImageTiffReader.open(mytif) do io
    description(io, 1)
end
print(desc)
# output
frameNumbers = 1
acquisitionNumbers = 1
frameNumberAcquisition = 1
frameTimestamps_sec = 0.000000
acqTriggerTimestamps_sec =
nextFileMarkerTimestamps_sec =
endOfAcquisition =  0
endOfAcquisitionMode = 0
dcOverVoltage = 0
epoch = [2016 6 4 13 51 7.8046]
```
