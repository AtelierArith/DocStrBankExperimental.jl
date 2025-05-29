```
getMeasurementsMotionCompFD(bMeas::MPIFile, motFreq, tmot, freq, frames, sigma,
                  samplingPrecision, windowType)
Averages over raw data corresponding to the same motion state and creates the virtual frames
```

  * bMeas:		Meas data
  * motFreq:		Array containing dominant motion frequencies for each patch and frame
  * tmot:			Array containing repetitions of the same state (frame,patch,period)
  * freq:			Selected frequencies for reconstruction
  * frames:       Selected frames
  * alpha:        Window width relative to the DF cycle.
  * samplingPrecision:	true: rounding motion period to sampling precision, false: rounding to DF period precision
  * window:		1: Hann window, 2:FT1A05, 3: Rectangle
