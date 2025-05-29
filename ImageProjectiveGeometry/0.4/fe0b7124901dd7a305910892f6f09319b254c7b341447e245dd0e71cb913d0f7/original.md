fastradial - Loy and Zelinski's fast radial feature detector

```
Usage: (S, So) = fastradial(img, radii, alpha=2, beta=0)

Arguments:
           img   - Image to be analysed
                   ::Array{T,2} or ::ImageMeta{T,2} 
           radii - Vector of integer radius values to be processed
                   suggested radii might be [1, 3, 5]
           alpha - Radial strictness parameter.
                   1 - slack, accepts features with bilateral symmetry.
                   2 - a reasonable compromise.
                   3 - strict, only accepts radial symmetry.
                       ... and you can go higher
           beta  - Gradient threshold.  Gradients below this threshold do
                   not contribute to symmetry measure, defaults to 0.

Returns    S     - Symmetry map.  Bright points with high symmetry are
                   marked with large positive values. Dark points of
                   high symmetry marked with large -ve values.
           So    - Symmetry map based on orientation only.
```

To localize points use nonmaxsuppts() on S, -S or abs(S) depending on what you are seeking to find.

A good algorithm for detecting eyes in face images.

If the input is an ImageMeta cimg will be an ImageMeta with property spatialorder set to ["y","x"].

Reference:   Loy, G.  Zelinsky, A.  Fast radial symmetry for detecting points of interest.  IEEE PAMI, Vol. 25, No. 8, August 2003. pp 959-973.
