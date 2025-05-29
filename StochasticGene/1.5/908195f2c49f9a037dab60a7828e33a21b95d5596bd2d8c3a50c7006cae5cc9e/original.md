```
RNADwellTimeData
```

Structure for storing RNA dwell time data.

# Fields

  * `label::String`: Label for the data set.
  * `gene::String`: Gene name (case sensitive).
  * `nRNA::Int`: Length of the histogram.
  * `histRNA::Array`: RNA histograms.
  * `bins::Vector{Vector}`: Number of live cell recording time bins.
  * `DwellTimes::Vector{Vector}`: Dwell times.
  * `DTtypes::Vector`: Types of dwell times.
