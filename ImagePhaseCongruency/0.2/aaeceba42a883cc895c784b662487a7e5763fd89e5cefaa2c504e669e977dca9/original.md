A phase congruent test image that interpolates from a step to a line.

Generates a test image where the feature type changes from a step edge to a line feature from top to bottom.  Gradient based edge detectors will only correctly mark the step-like feature towards the top of the image and incorrectly mark two features towards the bottom of the image whereas phase congruency will correctly mark a single feature from top to bottom.  In general, natural images contain a roughly uniform distribution of the full continuum of feature types from step to line.

```
Usage:
    img = step2line(sze; nscales=50, ampexponent=-1, ncycles=1.5, phasecycles=0.25)

Arguments:
      sze::Integer - Number of rows in test image, defaults to 512.

Keyword Arguments:
  nscales::Integer - No of Fourier components used to construct the signal.
                     Defaults to 50.
 ampexponent::Real - Decay exponent of amplitude with frequency.
                     A value of -1 will produce amplitude inversely
                     proportional to frequency (corresponds to step feature).
                     A value of -2 will result in the line feature
                     appearing as a triangular waveform. Defaults to -1.
     ncycles::Real - Number of wave cycles across the width of the image.
                     Defaults to 1.5
 phasecycles::Real - Number of feature type phase cycles going vertically
                     down the image. Defaults to 0.25 giving a sequence of feature
                     phase congruency angle varying from 0 to pi/2.
Returns:
   img::Array{Float64,2} - The test image.


Examples of use:
  > img = step2line()                              # Default pattern
  > img = step2line(ncycles=3, ampexponent=-1.5);  # 3 cycles, 'soft' step to line
  > img = step2line(ncycles=3, ampexponent=-1.5, phasecycles = 3);

```

See also:  [`circsine`](@ref), [`starsine`](@ref)
