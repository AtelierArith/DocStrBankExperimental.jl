```
io = csopen(containers[, mode="r"]; axis_lengths::Vector{Int}[, optional keyword arguments])
```

returns a handle to a CloudSeis data-set, and where `container::Container` corresponds to a dataset where all extents are in a single container, and  `container::Vector{<:Container}` corresponds to a dataset where extents are sharded across mulitple containers.  The container(s) can be either POSIX folders (container::Folder), or cloud storage container (e.g. container::AzContainer).

`mode` is one of `"r"` - read, `"w"` - write, `"r+"` - open existing data-set for reading and writing.

If `mode="w"`, then `axis_lenghts` is a required key-word argument.  `axis_lengths` specifies the size of the container.  The `axis_lengths` vector is of at-least length 3.

# Optional keyword arguments

  * `similarto::String` An existing CloudSeis dataset.  If set, then all other named arguments can be used to modify the data context that belongs to the existing CloudSeis dataset.
  * `history` history dictionary (see notes, below, for how it should be formatted/constructed).
  * `datatype::String` Examples are `CMP`, `SHOT`, etc.  If not set, then `UNKNOWN` is used.
  * `traceformat::DataType=Float32` Not supported.  We have only tested against `traceformat=Float32`.
  * `byteorder::String`
  * `extents::Vector{UnitRange}` List of integer ranges (frame range) for each extent.  Each extent maps to an object in block storage (set only one of `extents`, `frames_per_extent` and `mbytes_per_extent`).
  * `frames_per_extent::Int` Nominal number of frames per extent (set only one of `extents`, `frames_per_extent` and `mbytes_per_extent`).
  * `mbytes_per_extent::Int` Nominal size of each extent in units of mega-bytes (set only one of `extents`, `frames_per_extent` and `mbytes_per_extent`).
  * `geometry::Geometry` An optional three point geometry can be embedded in the CloudSeis file.
  * `tracepropertydefs::Vector{TracePropertyDef}` An array of trace property definitions.   These are in addition to the axes property definitions.
  * `dataproperties::Vector{DataProperty}` An array of data properties.  One property per dataset rather than one property per trace (as is true for `tracepropertydefs`).
  * `axis_propdefs::Vector{TracePropertyDef}` Trace properties corresponding to the CloudSeis axes.  If not set, then `SAMPLE`, `TRACE`, `FRAME`, `VOLUME` and `HYPRCUBE` are used.
  * `axis_units::Vector{String}` Units corresponding to the CloudSeis axes. e.g. `SECONDS`, `METERS`, etc.  If not set, then `UNKNOWN` is used.
  * `axis_domains::Vector{String}` Domains corresponding to the CloudSeis axes. e.g. `SPACE`, `TIME`, etc.  If not set, then `UNKNOWN` is used.
  * `axis_pstarts::Vector{Float64}` Physical origins for each axis.  If not set, then `0.0` is used for the physical origin of each axis.
  * `axis_pincs::Vector{Float64}` Physical deltas for each axis.  If not set, then `1.0` is used for the physical delta for each axis.
  * `axis_lstarts::Vector{Int}` Logical starts for each axis.  If not set, then `1` is used for the logical start for each axis.
  * `axis_lincs::Vector{Int}` Logical increments for each axis.  If not set, then `1` is used for the logical increment for each axis.
  * `compressor="leftjustify"` Compress the cache before writing to disk.  This is particularly useful for data with variable fold.  chooose from: ("none", "blosc", "leftjustify", "zfp", "cvx")
  * `compressor_options=()` Pass options as key-word arguments to the compression algorithm.  Currently, only `"zfp"` and `"cvx"` have options[1]

# Example

## Azure storage

```julia
using AzStorage, CloudSeis
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container, "w"; axis_lengths=[10,11,12], axis_pincs=[0.004,10.0,20.0])
close(io)
```

## POSIX storage

```
using AzStorage, FolderStorage
container = Folder("mydataset-cs")
io = csopen(container, "w"; axis_lengths=[10,11,12], axis_pincs=[0.004,10.0,20.0])
```

# Notes

  * When using the `similarto` option, one can change the number of dimensions of the data-set via `axis_lengths`.  If one shrinks the number of dimensions,

then various data-set properties (e.g. `axis_units`) will be truncated.  The truncation can be customized by using appropriate key-word arguments.

  * The zfp compression options are `tol`, `precision` and `rate`.  So, for example:

```
using AzStorage, CloudSeis
container = AzContainer("mydataset-cs"; storageaccount="mystorageacccount")
io = csopen(container, "w"; axis_lengths=[10,11,12], compressor="zfp", compressor_options=(tol=1e-4,))
```

Please refer to ZFPCompressor.jl for more information.  If `compressor_options` is not supplied, then the defaults are `(precision=16,)`.  Also, note that `compressor_options=()` results in ZFP lossless compression.  ZFP lossless compression will be used for the headers and foldmap regardless of the choice of `compressor_options`.

  * The cvx compression options are `b1`, `b2`, `b3` and `scale`.  So, for example:

```

```

Please refer to CvxCompress.jl for more information.  If `compressor_options` is no supplied, then the defaults are `(b1=16,b2=16,b3=16,scale=1e-2)`.

  * The history dictionary must follow a specific structure.  One can get the history from an existing data-set via `history(io::CSeis)`, and can

construct and/or agument history via `history!`.  In general the structure is,

```julia
Dict(
    "inputs" => [
        Dict(
            "container" => container, # dictionary describing where the input data-set is.
            "history" => history dictionary that, recursively, embeds the history of the input data-set.
        )
    ],
    "flow" => Dict(
        "flow" => Dict(
            "parameters" => flowparameters, # dictionary describing parameters that apply to all processes
            "processes" => [
                "process" => process, # dictionary or string that uniquely locates the process run
                "parameters" => parameters # dictionary describing parameters passed to the process
            ]
        )
    )
)
```
