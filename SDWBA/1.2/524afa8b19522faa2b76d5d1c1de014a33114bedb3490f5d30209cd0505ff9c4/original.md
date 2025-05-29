Scale the scatterer's size (overall or along a particular dimension) by a constant factor.

#### Parameters

  * `s` : Scatterer object.
  * `scale` : Factor by which to grow/shrink the scatterer.
  * `radius`, `x`, `y`, `z` : Optional factors, scaling the scatterer's radius

and along each dimension in space. All default to 1.0.

#### Returns

A rescaled scatterer.

#### Details

When making a scatterer larger, it is important to make sure it's body has enough segments to accurately represent the shape at the frequencies of interest. Specifically, the ratio L / (N λ), where L is the length of the animal, N is the number of segments, and λ is the acoustic wavelength, should remain constant, which may require interpolating new points between the existing ones. See Conti and Demer (2006) or Calise and Skaret (2011) for details.
