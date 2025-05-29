```
load_data(datatype, dttype, datapath, label, gene, datacond, traceinfo, temprna, datacol=3, zeromedian=false)
```

Load RNA or trace data based on the provided `datatype` string or symbol.

Supports multiple data formats, including steady-state RNA histograms, dwell time distributions, ON/OFF state durations, and fluorescence traces.

# Arguments

  * `datatype`: String or Symbol describing the data type (e.g. "rna", "tracegrid")
  * `dttype`: Dwell time type (used only for rnadwelltime and dwelltime)
  * `datapath`: Path(s) to the data file(s)
  * `label`: Label for the dataset
  * `gene`: Gene name
  * `datacond`: Experimental condition
  * `traceinfo`: Tuple of trace metadata
  * `temprna`: Integer divisor for histogram normalization
  * `datacol`: Column of trace data to extract (default = 3)
  * `zeromedian`: If true, zero-center each trace before fitting (default = false)

# Returns

  * A concrete data structure subtype (e.g., `RNAData`, `TraceRNAData`, `DwellTimeData`)

# Throws

  * `ArgumentError` if `datatype` is unsupported
