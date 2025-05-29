```
write_file(file, data, sample_rate, starttime, id; append=false, verbose_level=0, compress=:steim2, pubversion=1, record_length=nothing) -> n
```

Write `data` in miniSEED format to `file`, returning the number of records written `n`.  The number of samples per second  is given by `sample_rate`.

`starttime` is the date of the first sample, which must be a `Dates.DateTime`, or an integer number of nanoseconds since 1970-01-01T00:00:00.

`id` is an ASCII string giving the ID of the trace.  If it is longer than 64 characters, it is truncated with a warning.

!!! note
    The libmseed library requires `id` to be in the form `FDSN[:AGENCY]:NET_STA_LOC_BAND_SOURCE_POSITION`, where `NET` is the network, `STA` is the station, `LOC` is the instrumation location code, `BAND` is the frequency band of recording, `SOURCE` is the code for the kind of instrument, and `POSITION` gives the code for the component orientation.  `AGENCY` gives information about the source of the information, but this is not standard and other tools may not be able to read these IDs correctly.  The Federation of Digital Seismograph Networks (FDSN) describes the format at http://docs.fdsn.org/projects/source-identifiers/en/v1.0/ .

    For version 2 files (the default to write), the following character limits are in place:

      * `NET`: 2
      * `STA`: 5
      * `LOC`: 2
      * `BAND`, `SOURCE` and `POSITION`: 1

    For version 3 files, the total identifier must be less than 255 characters long.


Use `append=true` to add new records on to `file`; otherwise any existing file is overwritten.  `file` is created if it does not already exist in either case.

`verbose_level` is passed to the `libmseed` routine `mstl3_readtracelist` to control the verbosity level, with `0` (the default) only writing error messages to stderr, and higher numbers causing more information to be printed.

# Allowable `data` element types

miniSEED files can only contain data for `Int32`, `Float32` or `Float64` element types.  Therefore, this function will only write vectors with one of these element types and throw an error if a different type is passed in.  You should convert data to one of these types before calling this function.

# Compression options

`compress` can take the values `:steim1` or `:steim2`, causing the file to be written respectively with Steim-1 or Steim-2 compression.  Note that this is only possible for `Int32` data.

# miniSEED file version

The standard in-use version for miniSEED files is version 2, which is the default to write.  However the libmseed library supports the newer version 3. Note that version 2 only supports microsecond precision for times; if you pass a `starttime` which is not representable by a whole number of microseconds, the underlying libmseed library will truncate the time to the whole microsecond below the time given.

# All keyword arguments

  * `append = false`: If `true`, append this data to an existing file if it exists.
  * `verbose_level = 0`: Control verbosity of the libmseed library, with values greater than 0 increasing verbosity.
  * `compress = :steim2`: If input data are integers, use Steim compression when writing the data.  Options are: `:steim1` (Steim-1 compression) and `:steim2` (Steim-2) compression.
  * `pubversion = 1`: Set the publication version for the record.  In SEED, later versions correspond to revised data and are read from files in preference to earlier versions.
  * `record_length = nothing`: Control the record length of records written to disk.  By default the libmseed library determines the record length.
  * `version = 2`: miniSEED file version to write (can be `2` or `3`). Note that little other software supports the current version `3`, so the default is to write version `2`.

# Example

```
julia> using Dates: DateTime

julia> data = rand(Float32, 1000);

julia> sampling_rate = 100;

julia> starttime = DateTime("2000-01-01");

julia> id = "FDSN:GB_JSA__B_H_Z";

julia> LibMseed.write_file("data.mseed", data, sampling_rate, starttime, id)
1

julia> LibMseed.read_file("data.mseed")
MseedTraceList:
 1 trace:
  "FDSN:GB_JSA__B_H_Z": 2000-01-01T00:00:00.000000000 2000-01-01T00:00:09.990000000, 1 segments
```
