Generate a phase congruent circular sine wave grating.

Useful for testing the isotropy of response of a feature dectector.

```
Usage:    img = circsine(sze; wavelength = 40, nscales = 50, ampexponent = -1,
                          offset = 0, p = 2, trim = false)

Arguments:
   sze::Integer  - The size of the square image to be produced. Defaults to 512.

Keyword arguments:
 wavelength::Real - The wavelength in pixels of the sine wave. Defaults to 40.
 nscales::Integer - No of Fourier components used to construct the
                    signal. This is typically 1, if you want a simple sine
                    wave, or >50 if you want to build a phase congruent
                    waveform. Defaults to 50.
ampexponent::Real - Decay exponent of amplitude with frequency.
                    A value of -1 will produce amplitude inversely
                    proportional to frequency (this will produce a step
                    feature if offset is 0)
                    A value of -2 with an offset of pi/2 will result in a
                    triangular waveform.  Defaults to -1;
     offset::Real - Angle of phase congruency at which the features of the
                    star pattern will be generated at. This controls the feature type.
                    0 for a step-like feature, pi/2 for a line/triangular-like feature.
                    Defaults to 0. If nscales = 1 use pi/2 to get continuity
                    at the centre.
      p::Integer  - Optional parameter specifying the norm to use in
                    calculating the radius from the centre. This defaults to
                    2, resulting in a circular pattern.  Large values gives
                    a square pattern
      trim::Bool  - Optional boolean flag indicating whether you want the
                    circular pattern trimmed from the corners leaving
                    only complete circles. Defaults to false.
Returns:
   img::Array{Float64,2} - The test image.

Examples:
> circsine(nscales = 1) - A simple circular sine wave pattern
> circsine(nscales = 50, ampexponent = -1, offset =  0)     - Square waveform
> circsine(nscales = 50, ampexponent = -2, offset = pi/2)   - Triangular waveform
> circsine(nscales = 50, ampexponent = -1.5, offset = pi/4) - Something in between
                                                              square and triangular
> circsine(nscales = 50, ampexponent = -1.5, offset = 0)    - Looks like a square but is not.
```

See also: [`starsine`](@ref), [`step2line`](@ref)
