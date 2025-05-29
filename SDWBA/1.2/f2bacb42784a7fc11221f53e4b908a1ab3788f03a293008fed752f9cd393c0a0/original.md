Resample a scatterer's measurement points by interpolating between them. Used to change the resolution, for instance when increasing the scatterer's body size or decreasing the acoustic wavelength.

#### Parameters

  * `s` : Scatterer
  * `n` : Number of body segments desired in the interpolated scatterer.

#### Returns

A Scatterer with a different number of body segments.
