```
LucasKanade(Args...)
```

A differential method for optical flow estimation developed by Bruce D. Lucas and Takeo Kanade. It assumes that the flow is essentially constant in a local neighbourhood of the pixel under consideration, and solves the basic optical flow equations for all the pixels in that neighbourhood by the least squares criterion.

# Options

Various options for the fields of this type are described in more detail below.

## Choices for `iterations`

The termination criteria of the iterative search algorithm, that is, the number of iterations.

## Choices for `window_size`

Size of the search window at each pyramid level; the total size of the window used is 2*window_size + 1. If left unspecified, a default value of eleven is assumed.

## Choices for `pyramid_levels`

0-based maximal pyramid level number; if set to 0, pyramids are not used (single level), if set to 1, two levels are used, and so on. IF left unspecified, a default value of four is assumed.

## Choices for `eigenvalue_threshold`

The algorithm calculates the minimum eigenvalue of a (2 x 2) normal matrix of optical flow equations, divided by number of pixels in a window; if this value is less than `eigenvalue_threshold`, then a corresponding feature is filtered out and its flow is not processed (default value is 1e-4).

## `ϵ` termination criteria

Minimum required change in displacement at which the iterative algorithm continues to work. Default value is `1e-2`.

## References

1. B. D. Lucas, & Kanade. "An Interative Image Registration Technique with an Application to Stereo Vision," DARPA Image Understanding Workshop, pp 121-130, 1981.
2. J.-Y. Bouguet, “Pyramidal implementation of the afﬁne lucas-kanade feature tracker description of the algorithm,” Intel Corporation, vol. 5,no. 1-10, p. 4, 2001.
