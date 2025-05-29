```
EDF.SignalHeader
```

Type representing the header for a single EDF signal.

# Fields

  * `label::String`: the signal's type/sensor label, see https://www.edfplus.info/specs/edftexts.html#label
  * `transducer_type::String`: non-standardized transducer type information
  * `physical_dimension::String`: see https://www.edfplus.info/specs/edftexts.html#physidim
  * `physical_minimum::Float32`: physical minimum value of the signal
  * `physical_maximum::Float32`: physical maximum value of the signal
  * `digital_minimum::Float32`: minimum value of the signal that could occur in a data record
  * `digital_maximum::Float32`: maximum value of the signal that could occur in a data record
  * `prefilter::String`: non-standardized prefiltering information
  * `samples_per_record::Int32`: number of samples in a data record (NOT overall)
