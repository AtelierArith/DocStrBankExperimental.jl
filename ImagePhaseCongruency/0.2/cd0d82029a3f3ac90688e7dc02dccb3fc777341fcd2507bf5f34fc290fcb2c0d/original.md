Generate a phase congruent star shaped sine wave grating.

Useful for testing the behaviour of feature detectors at line junctions.

```
Usage:    img = starsine(sze; ncycles=10, nscales=50, ampexponent=-1, offset=0)

Argument:
     sze::Integer - The size of the square image to be produced. Defaults to 512.

Keyword arguments:
    ncycles::Real - The number of sine wave cycles around centre point.
                    Typically an integer, but any value can be used.
 nscales::Integer - No of fourier components used to construct the
                    signal. This is typically 1, if you want a simple sine
                    wave, or >50 if you want to build a phase congruent
                    waveform.  Defaults to 50.
ampexponent::Real - Decay exponent of amplitude with frequency.
                    A value of -1 will produce amplitude inversely
                    proportional to frequency (this will produce a step
                    feature if offset is 0)
                    A value of -2 with an offset of pi/2 will result in a
                    triangular waveform.
     offset::Real - Angle of phase congruency at which the features of the
                    star pattern will be generated at. This controls the feature type.
                    0 for a step-like feature, pi/2 for a line/triangular-like feature.
Returns:
   img::Array{Float64,2} - The test image.

Examples:
> starsine(nscales = 1) - A simple sine wave pattern radiating out
                          from the centre. Use 'offset' if you wish to
                          rotate it a bit.
> starsine(nscales = 50, ampexponent = -1, offset =  0)     - Square waveform
> starsine(nscales = 50, ampexponent = -2, offset = pi/2)   - Triangular waveform
> starsine(nscales = 50, ampexponent = -1.5, offset = pi/4) - Something in between
                                                              square and triangular
> starsine(nscales = 50, ampexponent = -1.5, offset = 0)    - Looks like a square but is not.
```

See also: [`circsine`](@ref), [`step2line`](@ref)
