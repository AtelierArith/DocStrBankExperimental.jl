```
SeisBandPass(in; <keyword arguments>)
```

Apply a bandpass filter to seismic data. Input and output data is 2D in tx domain. Filter is applied in fx domain.

# Arguments

  * `in`: Input 2D data array in tx domain. Time is first dimension.

# Keyword arguments

  * `dt=0.004`: time sampling interval in secs.
  * `fa=0`: lower frequency cut [Hz]
  * `fb=0`: lower frequency banpass [Hz]
  * `fc=60`: upper frequency bandpass [Hz]
  * `fd=80`: upper frequency cut [Hz]

# Example

```
julia> d = SeisLinearEvents(); SeisPlotAmplitude(d,125,0.004);
julia> d_filter = SeisBandPass(d;dt=0.004,fa=2,fb=8,fc=12,fd=20); SeisPlotAmplitude(d_filter,125,0.004)
julia> SeisPlot([d d_filter],title="Data and Filtered data")

```
