```
t = ISOtime2unix(ts::AbstractString) -> Float64
```

Take a string representing a time and return the equivalent Unix time. The `ts` string may take one of these forms:

  * "YYYY-mm-dd", or "YYYY-mm-ddThh", or "YYYY-mm-ddThh:mm", or "YYYY-mm-ddThh:mm:ss", or "dd-Jan-YY" or "dd-Jan-YYYY"

### Examples

```julia
using Dates
t = ISOtime2unix("2019-01-01T12")
1.546344e9

t = ISOtime2unix("25-Apr-1974")
1.3608e8
```
