```julia
antimarginal(newM, u0, mkd, newpartial)

```

If a marginal (statistics) of a probability reduce the dimensions (i.e. casts a shadow, or projects); then an  antimarginal aims to increase dimension of the probability within reason.

Notes

  * Marginalization is a integration of for higher dimension to lower dimension, so antimarginal likely involve  differentiation (anti-integral) instead.
  * In manifold language, this is an embedding into a higher dimensional space.
  * See structure from motion in machine vision, or stereo disparity for building depth clouds from 2D images.
  * Imagine combining three different partial embedding A=[1, nan, nan, 1.4], B=[nan,2.1,nan,4], C=[nan, nan, 3, nan] which should equal A+B+C = [notnan, notnan, notnan, notnan]
