A struct for the EEG data type. An EEG is simply conceived as a collection of labeled time series.

# Fields

  * `signals::Dict{String, TimeSeries}`: A dictionary mapping signal labels (strings) to arrays of floating-point values.

# Constructors

`EEG(file::String; id::String="")`: Instantiates an `EEG` from an EDF file (`file`).

# Example

```julia
eeg_data = EEG("path/to/edf_data/data.edf")
```
