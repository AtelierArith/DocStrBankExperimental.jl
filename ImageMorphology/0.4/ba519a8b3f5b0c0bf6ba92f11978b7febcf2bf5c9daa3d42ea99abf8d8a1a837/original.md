```
regional_maxima(img; [dims])
regional_maxima(img; se)
```

Determines all regional maxima of the `image`.

For grayscale image `img`, A regional maximum is defined as the connected set of pixels that have the same value, which is greater than the values of all pixels in direct neighborhood of the set.

The `dims` keyword is used to specify the dimension to process by constructing the box shape structuring element [`strel_box(img; dims)`](@ref strel_box). For generic structuring element, the half-size is expected to be either `0` or `1` along each dimension.

#Note This implementation is faster than maxtree local_maxima approach if maxtree not precomputed

# See also

The inplace version of this function is `regional_maxima!`.

# References

  * [1] L. Vincent, “Morphological grayscale reconstruction in image analysis: applications   and efficient algorithms,” IEEE Trans. on Image Process., vol. 2, no. 2, pp. 176–201, Apr.   1993, doi: 10.1109/83.217222.
  * [2] P. Soille, Morphological Image Analysis. Berlin, Heidelberg: Springer Berlin   Heidelberg, 2004. doi: 10.1007/978-3-662-05088-0.
