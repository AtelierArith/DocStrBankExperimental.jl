The `Epoch` type represents a single instant in time. It is used throughout the SatelliteDynamics module. It is meant to provide a clear definition of moments in time and provide a convenient interface display time in various representations as well as in differrent time systems. The internal data members are also chosen such that the representation maintains nanosecond-precision in reprersenation of time and doesn't accumulate floating-point arithmetic errors larger than nanoseconds even after centuries.

Supports `+`, `+=`, `-`, and `-=` operators. Two Epoch's can be differenced to return the time difference between two Epochs. If adding a `Real` number it is interpreted as an offset in seconds to add to the Epoch.

The class also supports all arithmetic operators: `==`, `!=`, `<`, `<=`, `>`, `>=`

Arguments:

  * `year::Real` Year
  * `month::Real` Month
  * `day::Real` Day
  * `hour::Real` Hour (optional)
  * `minute::Real` Minute (optional)
  * `second::Real` Seconds (optional)
  * `nanoseconds::Real` Nanoseconds (optional)
  * `tsys::String`: Time system of the epoch at initialization

The Epoch class can be also be initialized from a string. Examples of Valid String constructors are: 

```julia
epc = Epoch("2018-12-20")
epc = Epoch("2018-12-20T16:22:19.0Z")
epc = Epoch("2018-12-20T16:22:19.123Z")
epc = Epoch("2018-12-20T16:22:19.123456789Z")
epc = Epoch("2018-12-20T16:22:19Z")
epc = Epoch("20181220T162219Z")
epc = Epoch("2018-12-01 16:22:19 GPS")
epc = Epoch("2018-12-01 16:22:19.0 GPS")
epc = Epoch("2018-12-01 16:22:19.123 GPS")
epc = Epoch("2018-12-01 16:22:19.123456789 GPS")
```
