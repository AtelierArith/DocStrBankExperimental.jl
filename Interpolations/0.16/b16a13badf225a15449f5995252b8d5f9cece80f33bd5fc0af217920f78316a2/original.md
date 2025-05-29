`extrapolate(itp, scheme)` adds extrapolation behavior to an interpolation object, according to the provided scheme.

The scheme can take any of these values:

  * `Throw` - throws a BoundsError for out-of-bounds indices
  * `Flat` - for constant extrapolation, taking the closest in-bounds value
  * `Line` - linear extrapolation (the wrapped interpolation object must support gradient)
  * `Reflect` - reflecting extrapolation (indices must support `mod`)
  * `Periodic` - periodic extrapolation (indices must support `mod`)

You can also combine schemes in tuples. For example, the scheme `(Line(), Flat())` will use linear extrapolation in the first dimension, and constant in the second.

Finally, you can specify different extrapolation behavior in different direction. `((Line(),Flat()), Flat())` will extrapolate linearly in the first dimension if the index is too small, but use constant etrapolation if it is too large, and always use constant extrapolation in the second dimension.
