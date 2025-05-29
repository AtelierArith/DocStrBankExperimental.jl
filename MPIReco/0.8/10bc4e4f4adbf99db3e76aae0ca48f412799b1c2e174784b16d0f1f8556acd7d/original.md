```
reconstructionPeriodicMotion(bSF::MPIFile, bMeas::MPIFile, freq::Array{Int64,1};
			bEmpty=nothing, bgFrames=nothing,
			alpha::Float64=3.0, choosePeak::Int64=1, frames::UnitRange=1:acqNumFrames(bMeas),
			samplingPrecision::Bool=true, windowType::Int64=1,
			bSFFrequencyAnalysis::MPIFile=bSF,higherHarmonic::Int64=1,
			kargs...)

Performs multi-patch reconstruction of raw data from an object with periodic motion
```

  * bSF:			System functions for reconstruction
  * bMeas:		Raw data of the measurement
  * freq:                 Selected frequencies for reconstruction
  * bEmpty:		Background measurement
  * bgFrames:		Background frames
  * choosePeak:		Number of chosen peak for motion frequency
  * alpha:        	Window width relative to DF cycle
  * frames: 		Selected frame
  * lambda:		Regularization parameter for reconstruction
  * iterations:		Number of iterations
  * samplingPrecision:    true: rounding motion period to sampling precision, false: rounding to DF period precision
  * windowFunction:       1: Hann window, 2:FT1A05, 3: Rectangle
  * bSFFrequencyAnalysis: System function for frequency analysis
