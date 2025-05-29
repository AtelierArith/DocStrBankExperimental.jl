```
RNAOnOffData
```

Structure for storing RNA ON/OFF time data.

# Fields

  * `label::String`: Label for the data set.
  * `gene::String`: Gene name (case sensitive).
  * `nRNA::Int`: Length of the histogram.
  * `histRNA::Vector`: RNA histograms.
  * `bins::Vector`: Number of live cell recording time bins.
  * `ON::Vector`: ON time probability density.
  * `OFF::Vector`: OFF time probability density.
