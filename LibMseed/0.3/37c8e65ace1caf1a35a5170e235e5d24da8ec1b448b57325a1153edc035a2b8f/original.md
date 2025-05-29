```
read_buffer(buffer::Vector{UInt8}; channels::AbstractString, startdate::DateTime, enddate::DateTime, headers_only=false, time_tolerance=nothing, verbose_level=0) -> tracelist
```

Parse data in `buffer` (a series of bytes) as miniSEED data and return `tracelist` (a `MseedTraceList`) containing the data.

If `buffer` is not valid miniSEED data, then an error is thrown.

`channels` can contain a globbing pattern which matches the 'id' string of channels in the file, which will be of the form `"FDSN:NET_STA_CHA_BAND_SOURCE_POSITION"` (an FDSN Source ID; http://docs.fdsn.org/projects/source-identifiers/en/v1.0/). By default all channels are read.

To limit data approximately to the date range `startdate` to `enddate`, pass these as keyword arguments.  If only one of `startdate` or `enddate` are set, respectively, then the `enddate` and `startdate` is left open. The default is to read data from all time periods.

!!! Some data from before `startdate` or after `enddate` may be included     as only whole blocks are returned.  You will need to cut the data     after reading to ensure no samples outside the desired time window     are present.

If no records match `channels`, or all data for selected channels lie outside `startdate` to `enddate`, then an empty tracelist is returned.

By default, trace segments with gaps of less than half the nominal sampling interval are joined together to form a single segment.  This behaviour can be adjusted by passing a value in seconds to `time_tolerance`, in which case segments with gaps of less than `time_tolerance` s are joined.  Pass `time_tolerance = 0` to not merge segments with gaps.

!!! note
    `time_tolerance` can only be used on x86 and x64 platforms.  It is not possible to use it on PowerPC or ARM processors such as Apple Silicon ones. Users of these platforms will need to accept the default behaviour and manually join segments separated with gaps larger than the default tolerance.  See the note at https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/#Closure-cfunctions .


`verbose_level` is passed to the `libmseed` routine `mstl3_readbuffer` to control the verbosity level, with `0` (the default) only writing error messages to stderr, and higher numbers causing more information to be printed.
