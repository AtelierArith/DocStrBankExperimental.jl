dilate1d - 1D morphological dilation of a signal.

```
Usage:  df = dilate1d(f, k)

Arguments:  f - 1D array of values to be dilated
            k - Size of dilation kernel

Returns:   df - Array of dilated values
```

Note that if the size of the structuring element is even then the centre pixel is taken to be the integer pixel location to the right of the ideal.

This function uses Marcel van Herk's algorithm to run in linear time with respect to the length of the signal, irrespective of the structing element size.

See also: erode1d(), imdilate(), imerode()
