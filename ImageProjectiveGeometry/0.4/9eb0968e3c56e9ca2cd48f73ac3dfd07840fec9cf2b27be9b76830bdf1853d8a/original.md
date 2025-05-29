erode1d - 1D morphological erosion of a signal.

```
Usage:  ef = erode1d(f, k)

Arguments:  f - 1D array of values to be eroded
            k - Size of erosion kernel

Returns:   ef - Array of eroded values
```

Note that if the size of the structuring element is even then the centre pixel is taken to be the integer pixel location to the right of the ideal.

This function uses Marcel van Herk's algorithm to run in linear time with respect to the length of the signal, irrespective of the structing element size.

See also: dilate1d(), imerode(), imdilate()
